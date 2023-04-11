# Caesar-cipher
The program encrypt or decrypt (depends on your choice) an input text. The key (step) are required to input.

`code = ''

def choose_language(answer):

    russian_alphabet = 'абвгдежзийклмнопрстуфхцчшщъыьэюя'
    english_alphabet = 'abcdefghijklmnopqrstuvwxyz'
    if answer.lower() == 'en':
        return english_alphabet
    elif answer.lower() =='ru':
        return russian_alphabet
    
def is_valid_lang(answer2):

    while answer2.lower() != 'en' and answer2.lower() != 'ru':
        answer2 = input('Я Вас не понимаю, попробуйте выбрать язык еще раз') 
    if answer2.lower() == 'en' or answer2.lower() == 'ru':
        return answer2

def is_valid_ciph(num):

    while num != '1' and num != '2' and not num.isdigit():
        num = input('Попробуйте еще раз: 1 - зашифровать, 2 - расшифровать')
    if num == '1' or num == '2':
        num = int(num)
        return num   

def is_valid_key(n):

    while not n.isdigit():
        n = input('Введите целое число в качестве ключа ("сдвиг")')
    if n.isdigit():
        n = int(n)
        return n              

def base(i, ciph):
    
    if ciph == 1:    #зашифровать
        sym_ind = language.index(i) + key
        if sym_ind >= len(language):
            sym = language[sym_ind - len(language)]
            return sym
        else:
            sym = language[sym_ind] 
            return sym
        
    if ciph == 2:    #расшифровать 
        sym_ind = language.index(i) - key
        if sym_ind < 0:
            sym = language[len(language) + sym_ind]
            return sym
        else:
            sym = language[sym_ind]
            return sym

language_answ = input('Выберете язык. En - английский, Ru - русский')       
language_answ = is_valid_lang(language_answ)
language = choose_language(language_answ)

cipher = input('Вам нужно зашифровать текст или расшифровать? Нажмите 1 - зашифровать, 2 - расшифровать')
cipher = is_valid_ciph(cipher)

key = input('Введите шаг сдвига:')
key = is_valid_key(key)

text = input('Введите текст:') 

for c in text:
    if c in '.,-_!? ':
        code += c
    elif c.isupper():
        c = c.lower()
        code += base(c, cipher).upper()            
    else:  
        code += base(c, cipher) 

print(code)`

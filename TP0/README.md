Put your TP0 solution here
TP0 folder

number_map = {
    "0": "zero", "1": "one", "2": "two", "3": "three",
    "4": "four", "5": "five", "6": "six", "7": "seven",
    "8": "eight", "9": "nine", "10": "ten"
}

# punctuation 
punctuation = ".,!?;:"

def normalize_text(text):
    # 1. lowercase
    text = text.lower()
    
    # 2. punctuation
    clean_text = ""
    for char in text:
        if char not in punctuation:
            clean_text += char
    
    # 3. tokenization (split)
    words = clean_text.split()
    
    # 4. 
    normalized_words = []
    
    for word in words:
        
        if word in number_map:
            normalized_words.append(number_map[word])
        
        # إذا فيها رقم + نص (مثلا 7th)
        elif word.isdigit():
            normalized_words.append(number_map.get(word, word))
        
        else:
            normalized_words.append(word)
    
    
    return " ".join(normalized_words)




D1 = "Today she cooked 4 bourak. Later, she added two chamiyya and 1 pizza."
D2 = "Five pizza were ready, but 3 bourak burned!"
D3 = "We only had 8 chamiyya, no pizza, and one tea."
D4 = "Is 6 too much? I ate nine bourak lol"



print("D1:", normalize_text(D1))
print("D2:", normalize_text(D2))
print("D3:", normalize_text(D3))
print("D4:", normalize_text(D4))

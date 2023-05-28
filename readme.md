Измененный код функции с выводом 
хэша в двоичной системе счисления:

var calculateHash = (index, previousHash, timestamp, data, nonce) => {
var hash = CryptoJS.SHA256(index + previousHash + timestamp + data + nonce).toString();
var binaryHash = '';
for(var i = 0; i < hash.length; i++) {
binaryHash += parseInt(hash[i], 16).toString(2).padStart(4, '0');
}
return binaryHash;
};

Этот код определяет функцию `calculateHash`, которая принимает пять аргументов: `index` (индекс блока), `previousHash` (хеш предыдущего блока), `timestamp` (время создания блока), `data` (данные блока) и `nonce` (случайное число, используемое для получения хеша). 
Внутри функции создается хеш, используя библиотеку `CryptoJS` и алгоритм SHA-256. Затем этот хеш переводится в двоичную систему с помощью операции `parseInt` и функции `toString`. 
Для каждого символа в исходной строке хеша выполняется перевод в шестнадцатеричную систему, затем выполнение `parseInt` переводит его в двоичную систему с помощью `toString(2)`. Результаты каждого символа объединяются в строку `binaryHash`.
Затем функция возвращает двоичную строку хеша в переменной `binaryHash`. Эта функция является частью алгоритма Proof of Work для создания нового блока в блокчейне.


while (nextHash % 7 !==0){
    nonce++;
    nextTimestamp = new Date().getTime() / 1000;
    nextHash = calculateHash(nextIndex, previousBlock.hash,
        nextTimestamp, blockData, nonce)
    console.log("\"index\":" + nextIndex +
        ",\"previousHash\":"+previousBlock.hash+
        "\"timestamp\":"+nextTimestamp+",\"data\":"+blockData+
        ",\x1b[33mhash: " + nextHash + " \x1b[0m," +
        "\"difficulty\":"+difficulty+
        " \x1b[33mnonce: " + nonce + " \x1b[0m ");
}

Данный код содержит бесконечный цикл, который выполняет следующие действия:
1. Увеличивает значение переменной nonce на единицу.
2. Получает текущее время в секундах и записывает его в переменную nextTimestamp.
3. Вычисляет хеш нового блока, используя функцию calculateHash(), передавая ей значения nextIndex, previousBlock.hash, nextTimestamp, blockData и nonce в качестве параметров.
4. Если вычисленный хеш не кратен 7, то цикл продолжается с шага 1.
5. Если вычисленный хеш кратен 7, то данный блок считается действительным, и цикл прерывается. 



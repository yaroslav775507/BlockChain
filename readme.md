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

Данная функция будет возвращать хэш в виде строки из 256 символов, где каждый символ
- двоичный эквивалент соответствующего 
- шестнадцатеричного символа хэша.


Получаемый при условии того что хеш делится на 7

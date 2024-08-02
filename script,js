document.addEventListener("DOMContentLoaded", function() {
    generatePassword();
});

let passwordLength = 12;

function updateLength(value) {
    passwordLength = parseInt(value, 10);
    document.getElementById("lengthValue").textContent = passwordLength;
    generatePassword();
}

function generatePassword() {
    const charset = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*()_+~`|}{[]:;?><,./-=";
    let password = "";
    
    while (true) {
        password = "";
        for (let i = 0, n = charset.length; i < passwordLength; ++i) {
            password += charset.charAt(Math.floor(Math.random() * n));
        }
        
        if (isValidPassword(password)) {
            break;
        }
    }
    
    document.getElementById("password").textContent = password;
    copyToClipboard(password);
}

function isValidPassword(password) {
    const minLength = 8;
    const sequentialLimit = 4;
    const personalInfo = ["name", "email", "username"]; // Example personal info, update accordingly.
    const commonWords = ["password", "123456", "qwerty"]; // Add more common words as needed.

    if (password.length < minLength) return false;
    if (!/\d/.test(password)) return false;
    if (hasSequentialLetters(password, sequentialLimit)) return false;
    if (containsPersonalInfo(password, personalInfo)) return false;
    if (containsCommonWords(password, commonWords)) return false;

    return true;
}

function hasSequentialLetters(password, limit) {
    let count = 1;
    for (let i = 1; i < password.length; i++) {
        if (password.charCodeAt(i) === password.charCodeAt(i - 1) + 1) {
            count++;
            if (count >= limit) return true;
        } else {
            count = 1;
        }
    }
    return false;
}

function containsPersonalInfo(password, personalInfo) {
    for (const info of personalInfo) {
        if (password.toLowerCase().includes(info.toLowerCase())) {
            return true;
        }
    }
    return false;
}

function containsCommonWords(password, commonWords) {
    for (const word of commonWords) {
        if (password.toLowerCase().includes(word.toLowerCase())) {
            return true;
        }
    }
    return false;
}

function copyToClipboard(password) {
    const textarea = document.createElement("textarea");
    textarea.value = password || document.getElementById("password").textContent;
    document.body.appendChild(textarea);
    textarea.select();
    document.execCommand("copy");
    document.body.removeChild(textarea);
    alert("Password copied to clipboard!");
}

# roman-to-integer-js


function romanToInt(s) {
    // Step 1: Create a dictionary to map Roman numerals to numbers
    const romanToIntMap = {
        'I': 1,  // I means 1
        'V': 5,  // V means 5
        'X': 10, // X means 10
        'L': 50, // L means 50
        'C': 100, // C means 100
        'D': 500, // D means 500
        'M': 1000 // M means 1000
    };

    let total = 0;  // This will hold the final number
    let prevValue = 0;  // This keeps track of the last number we saw

    // Step 2: Loop through the Roman numeral string from back to front
    for (let i = s.length - 1; i >= 0; i--) {
        const currentValue = romanToIntMap[s[i]]; // Find the number for the current Roman numeral
        
        // Step 3: If the current number is smaller than the previous number, subtract it
        if (currentValue < prevValue) {
            total -= currentValue; // Subtract because smaller number comes before bigger number
        } else {
            total += currentValue; // Otherwise, just add the number
        }

        // Step 4: Update the previous number for the next loop
        prevValue = currentValue;
    }

    // Step 5: Return the final total
    return total;
}

// Example usage: Testing the function
console.log(romanToInt("III"));      // Output: 3 (1 + 1 + 1)
console.log(romanToInt("LVIII"));    // Output: 58 (50 + 5 + 1 + 1 + 1)
console.log(romanToInt("MCMXCIV"));  // Output: 1994

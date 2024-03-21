# SmartContract
// SPDX-License-Identifier : MIT
pragma solidity ^0.8.0;

library ArrayUtils {
    function sort(uint[] storage data) external {
    
        uint n = data.length;
        for (uint i = 0; i < n - 1; i++) {
            for (uint j = 0; j < n - i - 1; j++) {
                if (data[j] > data[j + 1]) {
                    (data[j], data[j + 1]) = (data[j + 1], data[j]);
                }
            }
        }
    }

    function removeDuplicates(uint[] storage data) external {
        uint length = data.length;
        if (length <= 1) return;

        uint newSize = 1;
        for (uint i = 1; i < length; i++) {
            bool duplicate = false;
            for (uint j = 0; j < newSize; j++) {
                if (data[i] == data[j]) {
                    duplicate = true;
                    break;
                }
            }
            if (!duplicate) {
                data[newSize] = data[i];
                newSize++;
            }
        }
    }
}


// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;


contract ArrayManipulation {
    using ArrayUtils for uint[];

    uint[] public dataArray;

    function addData(uint[] memory _data) public {
        dataArray = _data;
    }

    function sortData() public {
        dataArray.sort();
    }

    function removeDuplicates() public {
        dataArray.removeDuplicates();
    }
}

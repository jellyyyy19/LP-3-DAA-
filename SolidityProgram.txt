// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StudentData {
    struct Student {
        uint256 studentId;
        string name;
        uint256 age;
        string course;
    }

    Student[] public students;
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    function addStudent(uint256 _studentId, string memory _name, uint256 _age, string memory _course) public {
        require(msg.sender == owner, "Only the owner can add students");
        students.push(Student(_studentId, _name, _age, _course));
    }

    function getStudentCount() public view returns (uint256) {
        return students.length;
    }

    fallback() external {
        revert("Fallback function called. This contract does not accept Ether.");
    }
}


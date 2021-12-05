# Parallel & Distributed Programming 🏃‍♀️ 🏃‍♂️ 🏃 

## Goal

Several projects implementing various parallelism &amp; distribution concepts. 

## Project 1 - Non-Cooperative Multi-Threading

### Project Statement

_At a bank, we have to keep track of the balance of some accounts. Also, each account has an associated log (the list of records of operations performed on that account). Each operation record shall have a unique serial number, that is incremented for each operation performed in the bank._

_We have concurrently run transfer operations, to be executer on multiple threads. Each operation transfers a given amount of money from one account to someother account, and also appends the information about the transfer to the logs of both accounts._

_From time to time, as well as at the end of the program, a consistency check shall be executed. It shall verify that the amount of money in each account corresponds with the operations records associated to that account, and also that all operations on each account appear also in the logs of the source or destination of the transfer._

### TODO List

- [ ] Run concurrent operations 🏃‍♀️ 🏃‍♂️ 🏃 
- [ ] Perform conistency check at the end 🔚
- [ ] Perform consitency periodically ⏱

### Code Documentation

I need to implement a multi-threading environment in which each thread executes a specified number of random transactions between random accounts.

`Worker` is the model which handles everything related to a thread: spawning the tread, performing transactions, performing consistency checks, joining the thread.

Each `Worker` is passed a shared reference to the vector of `Accounts` the transactions are going to be performed on. For shared pointers, we can use Rc (_Refcounted_ or _Reference Counted Smart Pointers_). However, Rust compiler complains about that, since `Rc` is not in fact thread-safe. However, the solution for that is to use `Arc` instead (_Atomically Reference Counted_ smart pointers). 

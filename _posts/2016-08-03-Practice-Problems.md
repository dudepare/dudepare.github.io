---
layout: post
title: Practice Problems
category: programming
date: 2016-08-03
---

A large box can hold five items, while the small box can hold only one item. All items must be placed in boxes and used boxes have to be filled up completely. Write a function that calculates the minimum number of boxes needed to hold a given number of items. If it's not possible to meet the requirements, return -1.

Given 30 mins, I wasn't able to solve this the first time around. I thought the solution was complicated and needed some recursion mumbo jumbo. In short, I was not able to think clearly. I froze. I focused on the wrong thing -- I was so focused in putting code into the editor and for every run of the unittest, I hoped that it will pass. But hope is not really a good programming practice. You have to be 100% certain that it will work. You might tweak the code here and there but the logic should be clear.

So what did I do differently this time? Well, I paused and wrote my solution on paper first. Not all of my code but the meaty parts. How do I break down X items into groups. It turns out it was fairly straight forward. Fear just came over me first.

    import unittest
    class Boxes:
    
        @staticmethod
        def minimalNumberOfBoxes(products, availableLargeBoxes, availableSmallBoxes):
            usedLargeBoxes = 0
            usedSmallBoxes = 0
            sizeLarge = 5
            sizeSmall = 1
            while products >= sizeLarge and usedLargeBoxes < availableLargeBoxes:
                products -= sizeLarge
                usedLargeBoxes += 1
    
            while products >= sizeSmall and usedSmallBoxes < availableSmallBoxes:
                products -= sizeSmall
                usedSmallBoxes += 1
    
            if products == 0:
                return usedLargeBoxes + usedSmallBoxes
            else:
                return -1
    
    class TestBoxes(unittest.TestCase):
    
        def test_original(self):
            self.assertEqual(8, Boxes.minimalNumberOfBoxes(16, 2, 10))
    
        def test_10_items(self):
            self.assertEqual(6, Boxes.minimalNumberOfBoxes(10, 1, 10))
    
        def test_1_item(self):
            self.assertEqual(1, Boxes.minimalNumberOfBoxes(1, 2, 10))
    
        def test_1_item_nosol(self):
            self.assertEqual(-1, Boxes.minimalNumberOfBoxes(1, 2, 0))
    
        def test_11_items_nosol(self):
            self.assertEqual(-1, Boxes.minimalNumberOfBoxes(1, 2, 0))
    
        def test_2_items_nosol(self):
            self.assertEqual(-1, Boxes.minimalNumberOfBoxes(2, 2, 1))
    
        def test_zero(self):
            self.assertEqual(0, Boxes.minimalNumberOfBoxes(0, 0, 0))
    
    if __name__ == '__main__':
        unittest.main()

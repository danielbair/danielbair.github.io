#!/usr/bin/env/ python3
# -*- coding: utf-8 -*-
"""
~/.scripts/sgkconvertknu.py
the following script can be used in two modes, either as a python
module, or as a commandline utility.
as a commandline utility:
	usage: kconvertknu.py [-h] [-v] [infile] [outfile]

	this program takes a file written in Sgaw Karen KNU font, and converts it into
	Karen unicode

	positional arguments:
	  infile         the input file, if no file is provided, the script will run
					 tests instead
	  outfile        the output file, if output is not provided, the input file
					 will be overwriten

	optional arguments:
	  -h, --help     show this help message and exit
	  -v, --version  show program's version number and exit

	this script was written by Ben Sharon

as a python module:
	converter(input_str)
	this function takes an input_str contianing Karen text encoded with the KNU font,
	and returns a string with characters swaped to the coresponding unicode character.
	the proccess isn't perfect, because there is not a 100% 1 to 1 relationship
	between the two encodings. it is recommended to run the preprosessor first.
	that will improve the situation, although there is still some ambiguity. the
	following is a list of some of the known ambiguities:

		* wa followed by plersee (is a number and a colon, or the syllable 'wa')

	preprocessor(input_str)
	this funciton takes an input string and returns a string with some preprocessing in
	preparation for converter()


"""

prog_version = '1.1'

import re

def converter(input_str):
	char_map = {
		"H": "ံ", "h": "့", ";": "း", "=": "-", "<": ",",
		"I": ".", "$": ".", "“": "“", "?": "“",
		"/": "”", "A": " ", ":": "★", "0": "၀",
		"1": "၁", "2": "၂", "3": "၃", "4": "၄", "5": "၅",
		"6": "၆", "7": "၇", "8": "၈", "9": "၉", "u": "က",
		"c": "ခ", "*": "ဂ", "C": "ဃ", "]": "င", "p": "စ",
		"q": "ဆ", "Z": "ဇ", "n": "ည", "!": "ည", "w": "တ",
		"x": "ထ", "'": "ဒ", "e": "န", "E": "န", "M": "န့",
		"y": "ပ", "z": "ဖ", "b": "ဘ", "r": "မ", ",": "ယ",
		"s": "ျ", "V": "ျ့", "%": "ရ", "&": "ရ", "j": "ြ",
		"}": "ြ", "-": "ြ", "_": "ြ", "v": "လ", "F": "ၠ",
		"G": "ွ","U": "ွ့", "o": "သ", "[": "ဟ", "O": "ှ့",
		"+": "ှု", "t": "အ", "{": "ဧ", "g": "ါ", "m": "ာ်",
		"d": "ိ", "D": "ီ", "k": "ု", "K": "ု", "l": "ူ",
		"L": "ူ", "J": "ဲ", "X": "ၢ", ">": "ၢ်", "f": "်",
		".": "ၣ်", "R": "ၤ", "]": "=", "S": "ှ",
		"\u1AFD": ":",
	}

	output_str = ""
	for char in input_str:
		try:
			output_str += char_map[char]
		except KeyError:
			output_str += char
	return output_str

def preprocessor(knu_str):
	regex_rules = (
		("([j}_-])(.)", "\\2\\1"), 
		# Switch any ra's with the next character

		("0([dfghjklm.RSDFGHJX>])", "ဝ\\1"),
		# Change any wa's that appear to be part of a syllable ahead of
		# time. This will fix most of them, however, there is still an
		# ambiguity with wa's followed by plersee because knu also uses
		# plersee between numbers

		("([1234567890]);", "\\1\u1AFD")
		# Change any plersee following a number (other than zero,
		# because that's ambiguous) into an intermediate \u1AFD which
		# will then be changed into a colon in the main converter stage
	)

	for pat, repl in regex_rules:
		knu_str = re.sub(pat, repl, knu_str)

	return knu_str


def test():
	import unittest
	class TestSequenceFunctions(unittest.TestCase):

		def test_preprocessor_ra_switcher(self):
			self.assertEqual("uj", preprocessor("ju"))

		def test_preprocessor_wa_fixer(self):
			self.assertEqual("ဝg", preprocessor("0g"))

	suite = unittest.TestLoader().loadTestsFromTestCase(TestSequenceFunctions)
	unittest.TextTestRunner(verbosity = 2).run(suite)


if __name__ == "__main__":
	import argparse, sys

	parser = argparse.ArgumentParser(
	   description = 'this program takes a file written in Sgaw Karen KNU font, and converts it into Karen unicode',
	   epilog = 'this script was written by Ben Sharon')
	parser.add_argument('infile', nargs='?', action = "store", default = None, help = 'the input file, if no file is provided, the script will run tests instead')
	parser.add_argument('outfile', nargs='?', action = "store", default = None, help = 'the output file, if output is not provided, the input file will be overwriten')
	parser.add_argument('-v', '--version', action = 'version', version = prog_version)
	args = parser.parse_args()
	
	if args.infile:
		file_text = open(args.infile, 'r', encoding='utf-8').read()
		file_text = preprocessor(file_text)
		file_text = converter(file_text)
		
		if args.outfile:
			open(args.outfile, 'w', encoding='utf-8').write(file_text)
		else:
			open(args.infile, 'w', encoding='utf-8').write(file_text)

	else:
		test()
#!/usr/bin/env/ python3
# -*- coding: utf-8 -*-
"""
~/.scripts/sgkspellcheck.py

this module has two modes of operation, as a command line utility, and as a python module.
as a commandline utility:
	usage: sgkspellcheck.py [-h] [-v] [infile] [outfile]

	this script takes an input file, and looks for strings of Myanmar characters
	which do not make a valid Sgaw Karen syllable. if it finds any invalid syllables,
	it will print information about them it to the outfile.

	positional arguments:
	  infile         the input file, if no file is provided, the script will run
					 tests instead
	  outfile        the output file, default is stdout

	optional arguments:
	  -h, --help     show this help message and exit
	  -v, --version  show program's version number and exit

as a python module:
	parse_string_to_phrases(iterable)
	takes a string of text, and returns a list of all runs of Myanmar characters
	
	parse_phrase_to_syllables(sgk_phrase)
	takes a string of Myanmar characters, and returns a list of syllables
	
	check_syllable_spelling(syllable)
	takes a string containing a syllable, and determines whether it is a valid syllable or not

"""
import unicodedata, binascii

programVersion = '1.2'

class SyllableChecker:

	def __init__(self):

		self.consonants = set("ကခဂဃငစဆၡဇညတထဒနပဖဘမယရလဝသဟအဧ")
		self.medials = set("ြျှွၠ")
		self.vowels = set("ါံၢုူ့ဲိီ")
		self.tones = set("ၢၣးာၤ")
		self.asat = "်"
		self.numerals = set("၁၂၃၄၅၆၇၈၉၀")
		self.myanmarCharacters = (set({chr(x) for x in range(4096, 4256)}) | set({chr(x) for x in range(43616, 43644)}))
		self.medialCombatibilityMap = {
			"က": set("ွြၠျ"), "ခ": set("ွြၠျ"), "စ": set("ွြှ"), "ဆ": set("ွြှ"), "ည": set("ွ"), "တ": set("ွြ"),
			"ထ": set("ွြ"), "ဒ": set("ွ"), "န": set("ွ"), "ပ": set("ွြှၠျ"), "ဖ": set("ွြှၠျ"), "ဘ": set("ှၠျ"),
			"မ": set("ွှၠျ"), "ယ": set("ွ"), "ရ": set("ွ"), "လ": set("ွ"), "သ": set("ွြ"),
		}
		self.lastSyllable, self.errorLog = "", []

	def parseSyllables(self, string):
		syllable, inSyllable, lastCharacter = '', False, ''
		for currentCharacter in string:
			if not inSyllable and currentCharacter in self.myanmarCharacters:
				inSyllable = True; syllable += currentCharacter
			elif inSyllable and (
					currentCharacter in self.consonants or
						(lastCharacter not in self.numerals and currentCharacter in self.numerals) or
						(lastCharacter in self.numerals and currentCharacter not in self.numerals and currentCharacter in self.myanmarCharacters)
					):
				if syllable: yield syllable; syllable = currentCharacter
			elif inSyllable and currentCharacter in self.myanmarCharacters:
				syllable += currentCharacter
			else:
				inSyllable = False
				if syllable:
					yield syllable
					syllable = ''
			lastCharacter = currentCharacter
		if syllable: yield syllable

	def __charSetNumberAssignment(self, char):
		if char in self.consonants:
			return 1
		elif char in self.medials:
			return 2
		elif char in self.vowels:
			return 3
		elif char in self.tones:
			return 4
		elif char in self.asat:
			return 5
		return 0
		
	def isValidSyllable(self, syllable):
		isCorrect, self.lastSyllable, self.errorLog = True, syllable, []

		if not syllable:
			self.errorLog.append("oops, there's nothing here")
			return False

		if all(c in self.numerals for c in syllable):
			return isCorrect

		if syllable[0] not in self.consonants:
			self.errorLog.append("this syllable does not begin with a consonant")
			isCorrect = False

		if syllable[-1] in self.medials:
			self.errorLog.append("ends with a medial")
			isCorrect = False
		
		try:
			if syllable[1] in self.medials and syllable[1] not in self.medialCombatibilityMap[syllable[0]]:
				isCorrect = False
		except KeyError:
			self.errorLog.append("illegal combination of consonant and medial")
			isCorrect = False
		except IndexError: # A single character syllable, can't address the second character.
			pass

		if len(syllable) > 2 and syllable[-1] == self.asat and syllable[-2] not in 'ၣာၢ':
			self.errorLog.append("ahthee or hathee without asat")
			isCorrect = False

		s, c = syllable.replace("ၢ်", "်"), self.__charSetNumberAssignment
		if not all(c(s[i]) < c(s[i+1]) for i in range(len(s)-1)):
			self.errorLog.append("does not follow the basic structure of a syllable")
			isCorrect = False

		return isCorrect

	def stringContainsOnlyValidKarenSyllables(self, string):
		for syllable in self.parseSyllables(string):
			if not self.isValidSyllable(syllable):
				return False
		return True

	def getLastSyllableReport(self, verbosity = 3):
		reportMessage = 'Syllable Report\n'
		if verbosity == 1:
			reportMessage += '  Text: {}, Errors: {}'.format(self.lastSyllable, len(self.errorLog))
		elif verbosity > 1:
			reportMessage += '  Text: {}\n'.format(self.lastSyllable)
			if self.errorLog:
				reportMessage += '  Error Messages:\n'
				for errorMessage in self.errorLog:
					reportMessage += '    {}\n'.format(errorMessage)
		if verbosity > 2:
			reportMessage += "  Unicode Data (in syllable order):\n"
			for char in self.lastSyllable:
				reportMessage += '    U+{}: {}\n'.format(str(hex(ord(char))).replace('0x', '', 1).upper(), unicodedata.name(char, '<undefined>'))
		return reportMessage
# End SyllableChecker class
 
###################################################################################
# Test Code
###################################################################################

def test():
	import unittest, random
	class TestSequenceFunctions(unittest.TestCase):

		def setUp(self):
			self.checker = SyllableChecker()

		def test_validSyllable(self):
			testSyllables = ("တၢ်",)
#					"ဒီး", "ယွၤ", "ဟဲ", "လီၤ", "လၢ", "တၢ်", "အၢၣ်", "အ", "ပူၤ", "ဆၢ", "ထၢၣ်",
#					"အီၤ", "ဖဲ", "န့ၣ်", "ကိး", "ထီၣ်", "အ", "မံၤ", "လဲၤ", "မဲာ်", "ညါ", "က",
#					"စၢ်", "သး", "အိၣ်", "တၢ်", "ညီၤ", "ကီ", "ဘျုး", "ဖှိၣ်", "မ့ၢ်", "တီ", "အိၣ်",
#					"ဝဲ", "အါ", "မး", "ဟံး", "ဃာ်", "ဘျုး", "ပှၤ", "ထိ", "ဂီၢ်", "ပျၢ်",
#					"အၢ", "သီ", "သ", "ရူး", "မၣ်", "ဒဲး", "ဖိ", "အ", "ကျဲ", "ပှၤ", "ခ", "ရံာ်",
#			)
			for syllable in testSyllables:
				self.assertTrue(self.checker.isValidSyllable(syllable))

		def test_nonConsonantStart(self):
			testSyllables = (
					"ၤ", "ၢ်", "ံ", "ံဖံံ", "့တီ့", "ျကြျံၤ", "ျဒီိး", "ိကၤး", "ဲကျ",
			)
			for syllable in testSyllables:
				self.assertFalse(self.checker.isValidSyllable(syllable))

		def test_medialEnd(self):
			testSyllables = ("ကြ", "ကျ", "ကၠ", "ညြ", "တွ", "ဝှ",)
			for syllable in testSyllables:
				self.assertFalse(self.checker.isValidSyllable(syllable))

		def test_randomMyanmarSyllables(self):
			myanmarChars = ''.join((chr(x) for x in range(4096, 4256))) + ''.join((chr(x) for x in range(43616, 43644)))

			for i in range(30):
				for j in range(5):
					testStr = ''.join((random.choice(myanmarChars) for n in range(i)))
					try:
						self.checker.isValidSyllable(testStr)
					except Exception as e:
						self.fail("isValidSyllable('{}') unexpectedly raised an exception: ({})".format(testStr, e))

		def test_randomUnicodeSyllables(self):
			chars = ''.join((chr(x) for x in range(0, 65536)))

			for i in range(30):
				for j in range(5):
					testStr = ''.join((random.choice(chars) for n in range(i)))
					try:
						self.checker.isValidSyllable(testStr)
					except Exception as e:
						self.fail("isValidSyllable('{}') unexpectedly raised an exception: ({})".format(testStr, e))

		def test_parseSyllables(self):
			self.assertEqual("ဒီး-စီၤ-ဖံ-လံ-ပူး-စံး-ဘၣ်-အီၤ", '-'.join(self.checker.parseSyllables("ဒီးစီၤဖံလံပူးစံးဘၣ်အီၤ")))
			self.assertEqual("ဒီး-စီၤ-ဖံ-လံ-ပူး-စံး-ဘၣ်-အီၤ", '-'.join(self.checker.parseSyllables("somethingဒီးစီၤဖံလံပူးစံးဘၣ်အီၤ")))
			self.assertEqual("ဒီး-စီၤ-ဖံ-လံ-ပူး-စံး-ဘၣ်-အီၤ", '-'.join(self.checker.parseSyllables("ဒီးစီၤဖံလံပူးစံးဘၣ်အီၤsomething")))
			self.assertEqual("ဒီး-စီၤ-ဖံ-လံ-ပူး-စံး-ဘၣ်-အီၤ", '-'.join(self.checker.parseSyllables("ဒီးစီၤ ဖံလံပူးစံး ဘၣ်အီၤ")))

		def test_stringContainsOnlyValidKarenSyllables(self):
			self.assertTrue(self.checker.stringContainsOnlyValidKarenSyllables("ဒီးစီၤဖံလံပူးစံးဘၣ်အီၤ"))
			self.assertTrue(self.checker.stringContainsOnlyValidKarenSyllables("somethingဒီးစီၤဖံလံပူးစံးဘၣ်အီၤ"))
			self.assertTrue(self.checker.stringContainsOnlyValidKarenSyllables("ဒီးစီၤဖံလံပူးစံးဘၣ်အီၤsomething"))
			self.assertTrue(self.checker.stringContainsOnlyValidKarenSyllables("ဒီးစီၤ ဖံလံပူးစံး ဘၣ်အီၤ"))

			self.assertFalse(self.checker.stringContainsOnlyValidKarenSyllables("ဒီးစီၤဖံလံပူးးစံးဘၣ်အီၤ"))
			self.assertFalse(self.checker.stringContainsOnlyValidKarenSyllables("somethingံဒီးစီၤဖံလံပူးစံးဘၣ်အီၤ"))
			self.assertFalse(self.checker.stringContainsOnlyValidKarenSyllables("ဒီးစီၤဖံလံပူးစံးဘၣ်ကြအီၤsomething"))
			self.assertFalse(self.checker.stringContainsOnlyValidKarenSyllables("ဒီးစီၤ ဖံလံပူးစံး ဘၣ်အီၤ့"))
	
	suite = unittest.TestLoader().loadTestsFromTestCase(TestSequenceFunctions)
	unittest.TextTestRunner(verbosity = 2).run(suite)

###################################################################################
# Application Code
###################################################################################

if __name__ == "__main__":
	import argparse, sys

	parser = argparse.ArgumentParser(
	   description = 'this script takes an input file, and looks for strings of Myanmar characters which do not make a valid Sgaw Karen syllable',
	   epilog = 'this script was written by Ben Sharon')
	parser.add_argument('infile', nargs='?', action = "store", default = None, help = 'the input file, if no file is provided, the script will run tests instead')
	parser.add_argument('outfile', nargs='?', action = "store", default = None, help = 'the output file, default is stdout')
	parser.add_argument('-v', '--version', action = 'version', version = programVersion)
	args = parser.parse_args()
	
	if args.infile:
		input_text = open(args.infile, 'r').readlines()

		try:
			output_file = open(args.outfile, 'w')
		except TypeError:
			output_file = sys.stdout

		checker, errorNumber = SyllableChecker(), 0
		for i, line in enumerate(input_text):
			if not checker.stringContainsOnlyValidKarenSyllables(line):
				errorNumber += 1
				output_file.write("Error #{}: Spelling Error: Line {}:\n{}\n".format(errorNumber, i + 1, checker.getLastSyllableReport()))
		output_file.close()

	else:
		test()
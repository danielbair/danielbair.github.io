#!/usr/bin/env/ python3
# -*- coding: utf-8 -*-

prog_version = '1.1'

def insert(input_text, insert_char = "\u200b"):
	""""""
	karen_consonants = set("ကခဂဃငစဆၡဇညတထဒနပဖဘမယရလဝသဟအဧ")
	# Karen Consonants: before which we may insert a U+200b
	karen_chars = set({chr(x) for x in range(4096, 4256)}) | set({chr(x) for x in range(43616, 43644)})
	# Makes a set of all Myanmar characters

	opening_parentheses = set("([{")
	# parenthetic characters which may start a new line after karen text
	closing_parentheses = set(")]}")
	#characters after which a line my break if directly followed by a Karen consonant
	
	input_text = input_text.replace("\u200b", "")
	# Note, even though we're making the insert_char changable for test purposes, replacing any random character that comes in would be dangerous. So we'll leave the replace part as \u200b.


	output_text, last_char = [], ''
	for char in input_text:
		if char in karen_consonants and (last_char in karen_chars or last_char in closing_parentheses):
			output_text.append(insert_char + char)
		elif char in opening_parentheses and last_char in karen_chars:
			output_text.append(insert_char + char)
		else:
			output_text.append(char)
		last_char = char
	output_text = ''.join(output_text)
	corrections = (
		("ခ{}ရံာ်", "ခရံာ်"),
		("ပ{}တြၢၤ", "ပတြၢၤ"),
	)
	for old, new in corrections:
		output_text = output_text.replace(old.format(insert_char), new)
	return output_text

def test_insert():
	import unittest
	class TestSequenceFunctions(unittest.TestCase):
		def test_basic(self):
			data = "လံာ်စီဆှံအတၢ်ကွဲးအသးတဖၣ်န့ၣ်ဟဲလၢယွၤဆံးအါလဲၣ်."
			self.assertEqual("လံာ်-စီ-ဆှံ-အ-တၢ်-ကွဲး-အ-သး-တ-ဖၣ်-န့ၣ်-ဟဲ-လၢ-ယွၤ-ဆံး-အါ-လဲၣ်.", insert(data, "-"))

		def test_hkree(self):
			data = "ပှၤခရံာ်ဖိအကျဲ"
			self.assertEqual("ပှၤ-ခရံာ်-ဖိ-အ-ကျဲ", insert(data, "-"))

		def test_batrur(self):
			data = "လံာ်စံးထီၣ်ပတြၢၤအပူၤ"
			self.assertEqual("လံာ်-စံး-ထီၣ်-ပတြၢၤ-အ-ပူၤ", insert(data, "-"))

		def test_parentheses(self):
			data = "တၢ်ကွဲးအသးလၢ(လံာ်စံးထီၣ်ပတြၢၤ)အပူၤ"
			self.assertEqual("တၢ်-ကွဲး-အ-သး-လၢ-(လံာ်-စံး-ထီၣ်-ပတြၢၤ)-အ-ပူၤ", insert(data, "-"))
			data = "တၢ်ကွဲးအသးလၢ[လံာ်စံးထီၣ်ပတြၢၤ]အပူၤ"
			self.assertEqual("တၢ်-ကွဲး-အ-သး-လၢ-[လံာ်-စံး-ထီၣ်-ပတြၢၤ]-အ-ပူၤ", insert(data, "-"))
			data = "တၢ်ကွဲးအသးလၢ{လံာ်စံးထီၣ်ပတြၢၤ}အပူၤ"
			self.assertEqual("တၢ်-ကွဲး-အ-သး-လၢ-{လံာ်-စံး-ထီၣ်-ပတြၢၤ}-အ-ပူၤ", insert(data, "-"))
			data = "တၢ်[]ကွဲး{အ}သးလၢ{လံာ်စံး(ထီၣ်ပတြၢၤ}အပူၤ]"
			self.assertEqual("တၢ်-[]-ကွဲး-{အ}-သး-လၢ-{လံာ်-စံး-(ထီၣ်-ပတြၢၤ}-အ-ပူၤ]", insert(data, "-"))

		def test_latin(self):
			data = "တိနီၣ် – လံာ်စီဆှံOld Testemantအပူန့ၣ်လီၤ. လံာ်စီဆှံအသီတအိၣ်ဒံးဘၣ်."
			self.assertEqual("တိ-နီၣ် – လံာ်-စီ-ဆှံOld Testemantအ-ပူ-န့ၣ်-လီၤ. လံာ်-စီ-ဆှံ-အ-သီ-တ-အိၣ်-ဒံး-ဘၣ်.", insert(data, "-"))
			data = "ဖဲကစၢ်ယွၤစံးဝဲတၢ်,ကွဲးအ. သးန့ၣ်မ့ၢ်အစံးဝဲ"
			self.assertEqual("ဖဲ-က-စၢ်-ယွၤ-စံး-ဝဲ-တၢ်,ကွဲး-အ. သး-န့ၣ်-မ့ၢ်-အ-စံး-ဝဲ", insert(data, "-"))

	suite = unittest.TestLoader().loadTestsFromTestCase(TestSequenceFunctions)
	unittest.TextTestRunner(verbosity = 2).run(suite)

if __name__ == "__main__":
	import argparse, sys

	parser = argparse.ArgumentParser(
	   description = 'this program takes a string of text potentially containing Sgaw Karen Unicode and inserts U+200b before each consonant if that consonant is preceded by any character in the Myanmar Unicode block',
	   epilog = 'this script was written by Ben Sharon')
	parser.add_argument('infile', nargs='?', action = "store", default = None, help = 'the input file, default is stdin')
	parser.add_argument('outfile', nargs='?', action = "store", default = None, help = 'the output file, default is stdout')
	parser.add_argument('-v', '--version', action = 'version', version = prog_version)
	args = parser.parse_args()

	if args.infile:
		karen_text = open(args.infile, 'r').read()

		if args.outfile:
			open(args.outfile, 'w').write(insert(karen_text))
		else:
			open(args.infile, 'w').write(insert(karen_text))
	else:
		test_insert()
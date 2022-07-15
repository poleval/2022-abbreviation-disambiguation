# Abbreviation disambiguation

## Introduction
Abbreviations are often overlooked in many NLP pipelines, but are still an important point to tackle, especially in such applications as machine translation, named entity recognition, or text-to-speech systems. There are at least two practical challenges in processing abbreviations. The first is the ability to find the full, expanded dictionary form of an abbreviation. In many cases this may be done by a simple dictionary lookup, but
- the use of abbreviations is often unconventional and there are there is no complete list of all possible abbreviation uses,
- many of the abbreviations are ambiguous, that is the same abbreviation may have more than one meaning, translating to possibly different expanded forms.

As in many other NLP task, the disambiguation of abbreviations needs to include context and additional language knowledge to

The second challenge, which is specific to languages with rich morphology, such as Polish, is the necessity to produce the expanded form of an abbreviation in correct grammatical form, in concordance with the rest of the sentence.

## Task Description
The aim of the task to is to propose a method of disambiguating Polish language abbreviations. The method should be able to produce the expanded form the abbreviation, both in its base form and the inflected form.

### Dataset
#### Training data
In this task we provide a (rather small) training dataset, which includes:
 - the abbreviation,
 - expanded form of the abbreviation,
 - base form of the abbreviation,
 - context of the abbreviation, with the '<mask>' placeholder marking the place, in which the abbreviation originally appeared.

Example:
```csv
Skrót,Rozwinięcie,Forma bazowa,Kontekst
s.,sobota,sobota,"Karpaty Siepraw (n. 16).  IV liga, grupa wschodnia: Olimpia Wojnicz - Grybovia (<mask> 16), Orkan Szczyrzyc - Wolania Wola Rzędzińska (s. 16), Sandecja II Nowy Sącz -"
d.,dawniej,dawniej,"poinformowała w piątek na swej stronie internetowej rosyjska korporacja państwowa Rostech (<mask> Rostechnologii). Nie podano daty przechwycenia amerykańskiego drona.  „Dron MQ-5B,"
n.,niedziela,niedziela,11)  Gościbia - Piast (s. 16)  Wiślanka - Sęp (s. 16); Skawinka - pauza  Sęp - Gościbia (<mask> 16.30)  Piast - Hejnał (n. 17)  Orzeł - Jordan (n. 17)  Czarni - Nadwiślanka (s.
pkt. proc.,punktu procentowego,punkt procentowy,"proc. Kolejne 0,12 pkt. proc. wynika ze spadku popytu na polski eksport, a 0,08 <mask> z zaburzeń na rynku wewnętrznym” - oszacowali."
rp.pl.,rp.pl.,rp.pl.,Jutro rozpocznie się proces posła ruchu Palikota - dowiedziała się <mask> Biedroń został oskarżony o naruszenie nietykalności cielesnej funkcjonariusza policji
```

The participants are encouraged to collect and use additional training and dictionary data and to publish it after the competition.

#### Test data
The test data consists of only the abbreviation and the conext. The aim of the system is to provide the expanded and base forms of the abbreviation.

### Evaluation
Two accuracy measures will be calculated on the basis of provided submissions:
 - Af - the accuracy of provided expanded forms of abbreviations (exact string match, not including letter case),
 - Ab - the accuracy of provided base forms of abbreviations (exact string match, not including letter case).

Based on these measures, the final score will be calculated using a weighted average:
Acc = 0.25\*Af + 0.75\*Ab

### Metadata
Tags: poleval-2022

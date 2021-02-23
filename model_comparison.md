|                     | EstBERT  |        |          | RoBERTa  |        |          | No BERT  |        |          | Stanza   |        |          |
| ------------------- | -------- | ------ | -------- | -------- | ------ | -------- | -------- | ------ | -------- | -------- | ------ | -------- |
|                     | prec/acc | recall | f1-score | prec/acc | recall | f1-score | prec/acc | recall | f1-score | prec/acc | recall | f1-score |
| token\_acc          | 97.7%    | 99.14% | 98.41%   | 97.7%    | 99.14% | 98.41%   | 97.7%    | 99.14% | 98.41%   | 99.96%   | 99.96% | 99.96%   |
| sents               | 92.54%   | 91.44% | 91.99%   | **94.81%**   | **95.58%** | **95.20%**   | 89.56%   | 87.80% | 88.67%   | 94.71%   | 91.85% | 93.26%   |
| UAS                 | 86.21%   | 87.49% | 86.84%   | **88.08%**   | **89.38%** | **88.73%**   | 70.79%   | 71.84% | 71.31%   | 86.69%   | 86.68% | 86.69%   |
| LAS                 | 83.47%   | 84.71% | 84.09%   | **85.49%**   | **86.75%** | **86.11%**   | 62.71%   | 63.64% | 63.17%   | 83.63%   | 83.63% | 83.63%   |
| UPOS                | 94.69%   | 96.09% | 95.38%   | 95.43%   | 96.84% | 96.13%   | 88.09%   | 89.40% | 88.74%   | **97.19%**   | **97.18%** | **97.18%**   |
| UFeats              | 94.15%   | 95.55% | 94.84%   | 94.50%   | **95.90%** | 95.20%   | 77.88%   | 79.03% | 78.45%   | **95.77%**   | 95.76% | **95.80%**   |

### *dep_las_per_type*
|                     | EstBERT  |        |          | RoBERTa  |        |          | No BERT  |        |          | Stanza   |        |          |
| ------------------- | -------- | ------ | -------- | -------- | ------ | -------- | -------- | ------ | -------- | -------- | ------ | -------- |
|                     | prec/acc | recall | f1-score | prec/acc | recall | f1-score | prec/acc | recall | f1-score | prec/acc | recall | f1-score |
| advmod              | 77,76    | 78,47  | 78,11    | **79,09**    | **80,78**  | **79,92**    | 63,71    | 65,21  | 64,45    | 78,93    | 78,11  | 78,52    |
| parataxis           | 54,08    | 49,38  | 51,62    | 57,7     | 51,17  | 54,24    | 51,57    | 43,03  | 46,92    | **65,45**    | **59,31**  | **62,23**    |
| dep                 | 0        | 0      | 0        | 0        | 0      | 0        | 0        | 0      | 0        | 0        | 0      | 0        |
| root                | 90,65    | 89,58  | 90,11    | **91,23**    | **91,97**  | **91,6**     | 75,34    | 73,86  | 74,6     | 90,18    | 87,46  | 88,8     |
| csubj:cop           | **82,91**    | 80,17  | 81,51    | 76,76    | **90,08**  | **82,89**    | 67,59    | 60,33  | 63,76    | 72,79    | 88,43  | 79,85    |
| goeswith            | 0        | 0      | 0        | 0        | 0      | 0        | 0        | 0      | 0        | 0        | 0      | 0        |
| ccomp               | 83,1     | 85,76  | 84,41    | **86,99**    | **87,5**   | **87,25**    | 50,48    | 60,76  | 55,15    | 81,87    | 78,78  | 80,3     |
| nmod                | 81,39    | 86,11  | 83,69    | **83,83**    | **88,52**  | **86,11**    | 55,07    | 59,52  | 57,21    | 82,53    | 84,27  | 83,39    |
| discourse           | 41,67    | 53,19  | 46,73    | 45,28    | 51,06  | 48       | 32,26    | 21,28  | 25,64    | **81,25**    | **55,32**  | **65,82**    |
| mark                | 91,29    | 91,93  | 91,61    | **91,74**    | **92,25**  | **92**       | 76,24    | 76,9   | 76,57    | 88,35    | 89,12  | 88,73    |
| cc:preconj          | 60,98    | 64,1   | 62,5     | 60,53    | 58,97  | 59,74    | 60,61    | 51,28  | 55,56    | **70,27**    | **66,67**  | **68,42**    |
| csubj               | **85,32**    | 86,11  | 85,71    | 83,19    | **91,67**  | **87,22**    | 76,92    | 55,56  | 64,52    | 84,91    | 83,33  | 84,11    |
| flat:foreign        | **90,91**    | 27,03  | 41,67    | 51,16    | **59,46**  | **55**       | 0        | 0      | 0        | 65,38    | 45,95  | 53,97    |
| acl                 | 83,53    | 86,36  | 84,92    | **87,74**    | **88,9**   | **88,32**    | 57,45    | 43,18  | 49,3     | 86,36    | 80,43  | 83,29    |
| acl:relcl           | **80,69**    | 82,22  | **81,45**    | 79,32    | 81,59  | 80,44    | 69,73    | 74,6   | 72,09    | 61,32    | **82,54**  | 70,37    |
| vocative            | **50**       | 33,33  | **40**       | 25       | **44,44**  | 32       | 20       | 22,22  | 21,05    | 30,77    | 44,44  | 36,36    |
| fixed               | 51,11    | **74,19**  | 60,53    | 63,64    | 67,74  | 65,62    | 60,71    | 54,84  | 57,63    | **75,86**    | 70,97  | **73,33**    |
| nummod              | 61,62    | 79,28  | 69,35    | 65,28    | 79,28  | 71,6     | 63,16    | 69,19  | 66,04    | **85,53**    | **85,23**  | **85,38**    |
| list                | 0        | 0      | 0        | 0        | 0      | 0        | 0        | 0      | 0        | 0        | 0      | 0        |
| advmod              | 77,81    | 78,11  | 77,96    | **79,09**    | **80,78**  | **79,92**    | 63,71    | 65,21  | 64,45    | 78,93    | 78,11  | 78,52    |
| det                 | 84,41    | 83,79  | 84,1     | 86       | **86,63**  | **86,31**    | **73,85**    | 67,45  | 70,5     | 80,8     | 82,8   | 81,78    |
| compound:prt        | 86,65    | **93,14**  | 89,78    | **89,51**    | 90,44  | **89,97**    | 73,68    | 81,5   | 77,39    | 85,52    | 89,6   | 87,51    |
| appos               | 66,34    | 71,28  | 68,72    | **74,82**    | **81,38**  | **77,96**    | 47,64    | 53,72  | 50,5     | 69,47    | 72,61  | 71       |
| nsubj               | 91,58    | 92,84  | 92,21    | **93,47**    | **94,48**  | **93,97**    | 64,85    | 66,44  | 65,64    | 90,67    | 89,9   | 90,28    |
| xcomp               | **88,98**    | **86,9**   | **87,92**    | 87,94    | 86,43  | 87,18    | 50,72    | 54,6   | 52,59    | 83,78    | 83     | 83,39    |
| obj                 | 88,37    | 88,88  | 88,63    | **89,95**    | **90,36**  | **90,15**    | 52,67    | 49,32  | 50,94    | 83,51    | 84,78  | 84,14    |
| amod                | 80,31    | 84,61  | 82,41    | 82,5     | 87,18  | 84,78    | 52,58    | 58,65  | 55,45    | **91,93**    | **89,26**  | **90,57**    |
| nsubj:cop           | 78,41    | 83,4   | 80,83    | **81,97**    | **85,39**  | **83,64**    | 54,92    | 51,33  | 53,07    | 77,78    | 79,7   | 78,73    |
| cop                 | 84,38    | 87,6   | 85,96    | **86,59**    | **88,6**   | **87,58**    | 61,42    | 67,14  | 64,15    | 81,43    | 86,11  | 83,7     |
| orphan              | 37,5     | 13,64  | 20       | 36,36    | 18,18  | 24,24    | 5,88     | 2,27   | 3,28     | **45**       | **20,45**  | **28,12**    |
| obl                 | 81,84    | 80,3   | 81,06    | **83,37**    | **82,28**  | **82,82**    | 48,62    | 50,74  | 49,66    | 79,61    | 77,78  | 78,68    |
| aux                 | **95,48**    | 95,55  | **95,52**    | 95,08    | **95,77**  | 95,42    | 83,32    | 79,01  | 81,11    | 89,93    | 95,04  | 92,42    |
| compound            | **90,24**    | 86,05  | 88,1     | 88,1     | 86,05  | 87,06    | 87,5     | 81,4   | 84,34    | 88,64    | **90,7**   | **89,66**    |
| case                | 92,72    | 92,62  | 92,67    | **93,41**    | **93,61**  | **93,51**    | 83,22    | 80,29  | 81,73    | 89,13    | 91,19  | 90,15    |
| advcl               | 68,33    | 65,69  | 66,98    | **71,15**    | **68,49**  | **69,8**     | 38,99    | 35,94  | 37,4     | 67,12    | 63,36  | 65,19    |
| flat                | 80,87    | 85,47  | 83,1     | 88,4     | 91,47  | 89,91    | 73,85    | 78,52  | 76,11    | **88,6**     | **92,1**   | **90,32**    |
| conj                | 76,98    | 80,09  | 78,5     | **81,38**    | **83,32**  | **82,34**    | 52,49    | 58,84  | 55,48    | 76,41    | 78,76  | 77,57    |
| cc                  | 91,5     | 90,69  | 91,09    | **92,33**    | **91,38**  | **91,85**    | 76,76    | 75,85  | 76,3     | 89,97    | 88,42  | 89,19    |
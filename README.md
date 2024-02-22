# pacbiohifi_read_assimilator
a pacbiohifi read check for the quick view of the read types and making it easy for the fasta manipulations and read extractions. A much faster pacbiohifi read assimilator which converts the pacbiohifi reads to the fasta and the corrresponding extractions for the assembler. It also writes the pacbiohifi reads indivually so that you can remove certain reads of not interest. Much faster on iterations.No need of any installation or anything just simply run the following 
```

#!/bin/bash
# Universitat Potsdam
# Author Gaurav Sablok
# date: 2024-2-22
# a read checker for the pacbiohifi reads making seqtk working for the hifi
# it is completely based on the regular expression and it is absolutely fast
# started writing it before lunch and stuck at a point and while having lunch solved it
read -r -p "pacbiohifi reads:" reads

if [[ "${reads}" == "" ]]; then
  echo "cant process with the fasta manipulations"
fi

if [[ -f "${reads}" ]]; then
  sed "s/@/>@/g" "${reads}" >"${reads%.*}".head.fastq
fi

echo "storing ids on the run"
grep "^>" "${reads%.*}".head.fastq |
  sed "s/ /|/g" | cut -f 1 -d "|" | sed "s/>@//g" >fastaids.txt
cat fastaids.txt | while read line; do
  grep -A 1 "${line}" "${reads%.*}".head.fastq >"$line".pacbiohifi.fasta
done

echo "all the pacbiohifi reads are stored as independent fasta files"
cat *.pacbiohifi.fasta >assimilated.pacbiohifi.fasta
echo "the assimilated pacbiohifi fasta is present in pacbiohifi.fasta"
echo "the fastaids for the all pacbiohifi are present in the fastaids.txt"
echo "thank you for using the pacbiohifi fastq fasta read assimilator"
echo "UNIVERSITAT POTSDAM"
```
Gaurav Sablok \
Academic Staff Member \
Bioinformatics \
Institute for Biochemistry and Biology \
University of Potsdam \
Potsdam,Germany \

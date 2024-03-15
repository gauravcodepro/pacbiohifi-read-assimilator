# pacbiohifi_read_assimilator
a pacbiohifi read check for the quick view of the read types and making it easy for the fasta manipulations and read extractions. A much faster pacbiohifi read assimilator which converts the pacbiohifi reads to the fasta and the corrresponding extractions for the assembler. It also writes the pacbiohifi reads indivually so that you can remove certain reads of not interest. Much faster on iterations.No need of any installation or anything just simply run the following. It follows a regular expression using the sed replacement to chunk the cached regular expression without writing it down and reading it again to make it faster. read this in rust as: 
```
use std::process:Command;
fn main(){
   Command::new("readreader.sh")
           .spawn()
           .expect("failed to execute command");
}
```
Gaurav Sablok \
Academic Staff Member \
Bioinformatics \
Institute for Biochemistry and Biology \
University of Potsdam \
Potsdam,Germany \

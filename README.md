# countbases
计算非softclip部分的碱基个数，输入文件为bam的cigar值
import re,sys

f1= open(sys.argv[1],'r')

n=0#bases

for line in f1:
        #if 'H' in line.strip():
        #       continue
        pattern1 = re.compile(r'\d+')
        pattern2 = re.compile(r'[A-Z]')
        base = pattern1.findall(line.strip())
        cig = pattern2.findall(line.strip())
        print base,cig
        for each in range(0,len(cig)):
                if cig[each] != 'S' and cig[each] != 'H':
                        n +=int(base[each])
print n

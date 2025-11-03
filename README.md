# test
scarica git ewindows e visual code
open git usando clicca su desktop (spazio è informativo in bioinf)
per aprire git bash in visual studio vai in new terminal e seleziona git bash
ls (list) comando per lista oggetti
mkdir (make directory) sia posizionale (nome doposcritto dopo sarà nome cartella)
cd (apre cartella) indica nome cartella da aprire
evitare simbolo tilde, indica home, slash indica path
 flag sono piccole stringhe precedute da dash, inidcano quale informazione vogliamo attivare
 mkdir -p test1/test2 (-p inidca crea parent se assenti, slash indica creaimo una cartella dentro altra)
 .. vuol dire indietro, cd da solo torna indietro a home
file read me in git hub (questo) è il file che indica cosa c'è dentro, in quello del dottorando c'è lista https://github.com/MirkMart/Lab_CompGeno
bash verràusato per costruire outline (input e utput) obiettivo è modificare input per essere leggibili, non faccimao programma
invia report git hub per esame (in genome papaer allega link git hub)
creare SSH key, non usare ctrl+c ma usa ctrl+shift+c (se no blocca processi) usare stessa mail account git hub ssh-keygen -t ed25519 -C "your_email@example.com"
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=linux
ho salvato chiave in utenti lucabolognini/ssh
segui procedura inidcate nella pagina di github
dopo aver creato cartella ssh, produci chiave pubblica  cd .ssh, ls, cat, e aggiungi chiave al tuo account git hub in settings
usa "" per aprire nomi con spazi

(2025 bash) nomachine per collegarsi 
entra in sangiacomobigea, nuovo desktop, crea sessione personalizzzta, esegui console,
creare nuova chiave ssh (nuova macchina a cui siamo collegati)

seleaziona directory (cd) test/
git status
ct README.md (legge file)
touch test1/test2/test3/README.md
../i (indietro)
nano apre modifica file


#FILE in nano script :
#!/bin/bash

# Mapping short reads on assembly. Mutate SAM into BAM

# Short reads
minimap2 -ax sr --MD -t 6 Anoste_raw.fasta SRR11672503_1_paired.fastq SRR11672503_2_paired.fastq > Anoste_raw_sr.sam
samtools view -Sb Anoste_raw_sr.sam > Anoste_raw_sr.bam
rm Anoste_raw_sr.sam
samtools sort -@6 -o Anoste_raw_sr_sorted.bam Anoste_raw_sr.bam
samtools index Anoste_raw_sr_sorted.bam
rm Anoste_raw_sr.bam 

# Long  reads
minimap2 -ax map-pb --MD -t 6 Anoste_raw.fasta SRR11672506.fastq.gz > Anoste_raw_lr.sam
samtools view -Sb Anoste_raw_lr.sam > Anoste_raw_lr.bam
rm Anoste_raw_lr.sam
samtools sort -@6 -o Anoste_raw_lr_sorted.bam Anoste_raw_lr.bam                        
samtools index Anoste_raw_lr_sorted.bam
rm Anoste_raw_lr.bam

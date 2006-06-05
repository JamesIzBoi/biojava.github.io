---
title: BioJava:CookbookPortuguese:SeqIO:WriteInFasta
---

Como eu imprimo uma sequencia no formato Fasta?
-----------------------------------------------

O formato FASTA é uma saída padrão de bioinformatics por ser conveniente
e fácil ler. O BioJava tem uma classe de ferramentas chamado SeqIOTools
que provê métodos estáticos de conveniência para executar várias tarefas
comums de IO da bioinformatica. Os trechos que se seguem, demonstram
como imprimir uma Sequence ou até mesmo um SequenceDB inteiro em formato
FASTA em um OutputStream como System.out. Todos os métodos de WriteXX de
SeqIOTools tem um OutputStream como um argumento. Deste modo você pode
enviar a sucessão recentemente formatada para um arquivo ou outro método
ou STDOUT, STDERR etc.

SeqIOTools está no package org.biojava.bio.seq.io

### Imprimindo uma SequenceDB

<java>

`     //cria uma instancia de SequenceDB interface`  
`     SequenceDB db = new HashSequenceDB();`

`     //adiciona as sequencias para o DB`  
`     db.addSequence(seq1);`  
`     db.addSequence(seq2);`

`     /*`  
`      * agora imprime para um output stream no formato FASTA usando um método estatico`  
`      * da classe de utilitário SeqIOTools. Neste caso nosso output stream é`  
`      * STDOUT`  
`      */`  
`     SeqIOTools.writeFasta(System.out, db);`

</java>

### Imprimindo de uma SequenceIterator

Muitos métodos readXXX() de SeqIOTools retornam um SequenceIterator que
itera em cima de todas as Sequences de um arquivo. A maioria dos métodos
writeXXX() de SeqIOTools tem uma versão dos métodos que recebem um
SequenceIterator como argumento. ex:

<java>

`     SequenceIterator iter =`  
`         (SequenceIterator)SeqIOTools.fileToBiojava(fileType, br);`

`     // e agora escreve tudo para FASTA, (você pode escrever em `  
`     // qualquer OutputStream, não apenas System.out)`  
`     SeqIOTools.writeFasta(System.out, iter);`

</java>

### Imprimindo uma única Sequence

<java>

`     /*`  
`      * SeqIOTools também possui um método que recebe uma única sequencia `  
`      * assim você não tem que fazer um SequenceDB`  
`      */`  
`     SeqIOTools.writeFasta(System.out, seq1);`

</java>
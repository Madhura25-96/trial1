

# Virtual Labs Experiment-1, Part-2: Linear Block Codes

## Theory: Experiment-1, Part-2

![alt text](https://github.com/Madhura25-96/trial1/blob/main/exp1.png)


Channel codes (or error correcting codes) are used in any digital communication sys-

tem to provide a reliable communication over a noisy communication channel. Figure

1 shows a part of a digital communication system focusing on the channel encoder-

decoder (refer Chapter 1 of [1] for a detailed description of a digital communication

system). Suppose the transmitter wants to send a bit-stream over a noisy communica-

tion channel. A communication channel may corrupt this bit-stream. To combat these

errors introduced by the channel, a channel encoder is used at the transmitter. The

channel encoder adds redundant bits to this input bit-stream that help the receiver to

recover (decode) the corrupted bit-stream.

In Part-2 of Experiment-1, we shall introduce binary block channel codes, referred

to as block codes from now on. We shall provide the deﬁnition of block codes and then

consider a subclass of block codes, linear block codes, that satisfy the linearity property.

We shall introduce two simple yet important families of block codes, repetition (REP)

and single parity check (SPC) codes. Through examples of REP and SPC codes, we

shall demonstrate how channel codes can be used to combat the errors introduced the

noisy communication channel. For a detailed discussion of the topics, please refer [1]-[3].

In the remaining part, we shall discuss the following topics:

• Introduction to linear block codes

• Repetition (REP) codes

• Single parity check (SPC) codes

1.1 Introduction to linear block codes

Let Fn denotes the vector space of all n-tuples over the ﬁnite ﬁeld F . Basics of

2

2

ﬁnite ﬁelds and vector spaces can be found in Part-1 of this experiment. For block

codes, the input bit-stream is ﬁrst divided into vectors of length k. Thus the input to a

channel encoder is a sequence of vectors of length k, also termed as message sequence.

1





Let u ∈ Fk denotes one such k-length message vector. To each message u, a block

2

encoder assigns a vector v ∈ Fn of length n > k, according to some rule. This vector v

2

is termed as the codeword corresponding to message u. Suppose there are M distinct

messages. A deﬁnition of a block code is given below.

Deﬁnition 1 (Block code C(n, M)): Consider any map (rule) that assigns a codeword

vector v ∈ Fn to the given message vector u ∈ Fk, where n > k. Then the set of

2

codewords corresponding to the given set of M distinct messages is termed as a block

2

code (or a codebook). The parameter n is called as the length of the code.

In general note that, the map associated with the a block code need not be one-

to-one, i.e., the codewords corresponding to distinct messages need not be distinct.

However for the purpose of this lab, we shall focus on the maps where there is a one-

to-one correspondence between a message and codeword. Let us consider an example

ꢀꢁ

ꢂ ꢁ

ꢂ

ꢂꢃ

for a block code. Let 0 1 , 1 1 be the set of distinct messages that a transmit-

ꢁ

ꢂ

ter wishes to transmit. Consider the map that assigns the vector 0 1 1 1 to the

ꢁ

ꢂ

ꢁ

ꢂ

ꢁ

ꢂ

message 0 1 and the vector 1 1 0 1 to the message 1 1 . Then the vectors

ꢁ

ꢂ

ꢁ

0 1 1 1 and 1 1 0 1 are termed as the codewords corresponding to the mes-

ꢁ

ꢂ

ꢁ

ꢂ

ꢀꢁ

ꢂ ꢁ

ꢂꢃ

sages 0 1 and 1 1 respectively and C(4, 2) = 0 1 1 1 , 1 1 0 1 is the

corresponding codebook or block code.

Note that a binary vector u ∈ Fk can take 2k possible distinct values. For linear block

2

codes, all possible 2k vectors in Fk comprises the set of distinct messages. However,

2

for linear block codes the map assigning messages to codeword cannot be arbitrary.

For linear block codes, as the name suggests, this map should be linear, i.e., it should

satisfy the property that addition of any two codewords should also be a codeword. A

deﬁnition of a linear block code is given below [1, Deﬁnition 3.1].

Deﬁnition 2 (Linear block code C(n, k)): A block code of length n and 2k codewords

is called as a linear block code if and only if its 2k codewords form a k-dimensional

subspace of the vector space F2n. The parameters n and k are called as the length and

dimension of a linear block code respectively.

Let us consider an example for a linear block code for k = 2. For k = 2, the

ꢀꢁ

ꢂ

ꢁ

ꢂ

ꢁ

ꢂ ꢁ

ꢂꢃ

set of messages will be 0 0 , { 0 1 , { 1 0 , 1 1 . Consider the map that as-

ꢀꢁ

ꢂ

ꢁ

ꢂ

ꢁ

ꢂ ꢁ

ꢂꢃ

signs codewords 0 0 0 , { 0 1 1 , { 1 0 1 , 1 1 0 to these messages re-

spectively. It can be veriﬁed that that this map is a linear and the set of codewords

form a 2-dimensional subspace of F3.

2

We shall next deﬁne the Hamming weight of a vector v ∈ Fn and the Hamming

2

distance between any two vectors v and v in Fn. These notions will be used to deﬁne

1

the minimum distance of a block code.

2

2

Deﬁnition 3 (Hamming weight of a vector): The Hamming weight of a vector ≿ ∈ Fn

2

is deﬁned as the number of non-zero components in it.

Deﬁnition 4 (Hamming distance d (v , v ) between vectors v and v ): The Ham-

2

H

1

2

1

ming distance between vectors v and v in Fn is deﬁned as the number of position these

1

two vectors diﬀer from each other.

2

2

ꢁ

ꢂ

For example, the Hamming weight of the vector v = 1 0 0 1 1 ∈ F5 is equal

ꢁ

ꢂ

ꢁ

ꢂ

2

to 3. For the vectors v = 1 0 0 1 1 and v = 1 0 0 0 0 , the Hamming

1

distance d (v , v ) = 2. We shall next deﬁne the minimum distance of a block code.

2

H

1

2

2





Deﬁnition 5 (Minimum distance dmin of a block code C(n, M)): The minimum dis-

tance dmin of the given block code is deﬁned as the minimum Hamming distance between

any two codewords of the code, i.e.,

dmin := min {d (v , v ) such that v , v ∈ C(n, M)} .

H

1

2

1

2

For the linear blocks it can be proved that, the minimum distance is equal the

minimum Hamming weight of a non-zero codeword. A linear block code of length n,

dimension k, and minimum distance dmin is denoted by C(n, k, dmin).

We shall next discuss two families of linear block codes; repetition and single parity

check codes.

1.2 Repetition codes

Repetition codes are one of the simplest yet important class of linear block codes.

For repetition codes we have k = 1, i.e., a message can either be 0 or 1. For the

repetition code of length n (REP-n code), as the name suggests, the message to be

transmitted is repeated n times. Thus the codewords corresponding to the messages 0

ꢁ

ꢂ

ꢁ

ꢂ

and 1 are 0 0 . . . 0 and 1 1 . . . 1 respectively. For example, the codewords

ꢀꢁ

ꢂ ꢁ

ꢂꢃ

of REP-5 are given by 0 0 0 0 0 , 1 1 1 1 1 . Typically the length n of

the repetition code is chosen to be an odd integer since an odd length is suitable

for majority logic decoding of repetition codes when the noise is introduced a binary

symmetric channel of cross-over probability p, denoted by BSC(p). A few preliminaries

about the binary symmetric channel are summarized in Remark 1.

Remark 1 (Binary symmetric channel (BSC(p))): In this remark, we shall describe

how noise is modeled according to the binary symmetric channel. As shown in Figure

2 for BSC(p), a transmitted bit is ﬂipped independently with probability p.

1 − p

0

1

0

1

p

p

1 − p

Figure 2: Binary symmetric channel with cross-over probability p

Without loss of generality we assume that p < 1/2, since when p > 1/2, one can

ﬁrst ﬂip the entire received bit sequence and use the decoding algorithms developed for

ꢁ

ꢂ

the the case when p < 1/2. For example, when a vector 0 1 1 is transmitted over

ꢁ

ꢂ

BSC(p), the probability of receiving the vector 1 1 0 is equal to p2(1 − p) since the

ﬁrst and the third bits are ﬂipped, whereas the second bit is not ﬂipped. Note that a

transmitted vector can get ﬂipped to any vector in Fn.

2

We shall now describe majority logic decoding for repetition codes of odd lengths

and illustrate how repetition codes can help to correct the errors introduced by a BSC.

First note that, a transmitted codeword can get ﬂipped to any vector in F2n (see Remark

1). According to majority logic decoding, the received vector y ∈ Fn is decoded as 1 is

2

the number of 1’s are in it are in majority, otherwise it is decoded as 0. For example,

ꢁ

ꢂ

for REP-3 code, when received vector is y = 1 1 0 , the decoded message is 1, since

the bit is in majority in this y.

3





1.3 Single parity check codes

In progress!!

Pre-quiz

\1.

Post-quiz

\1. The set of vectors {10101, 10010, 01110, 11111, 11000} correspond to linear or non-

linear block code?

(A) Linear block code

(B) Non-linear block code

Answer: (B)

\2. The encoded the message sequence 0 1 0 using REP-7 code is given by

(A) 0 0 0 0 0 0 0 1 1 1 1 1 1 1 0 0 0 0 0 0 0

(B) 0 0 0 0 0 1 1 1 1 1 0 0 0 0 0

(C) 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0 0 0

(D) None of the above

Answer: (A)

\3. The encoded the message sequence 1 0 0 0 1 0 1 1 0 1 1 1 using SPC(4, 3) code

is given by

(A) 1 0 0 0 1 1 0 1 1 1 0 1 1 1 1

(B) 1 0 0 0 0 1 0 1 1 1 0 1 1 1 0

(C) 1 0 0 1 0 1 0 1 1 1 0 0 1 1 1 1

(D) 1 0 0 1 0 1 0 1 0 1 0 0 0 1 1 1

Answer: (C)

References

[1] S. Lin and D. Costello, “Error Control Coding”, 2nd ed., Englewood Cliﬀs, New

Jersey, USA: Prentice-Hall, 2004.

[2] F. MacWilliams and N. Sloane, “The Theory of Error Correcting Codes”, Amster-

dam: North-Holland Publishing Company, 1977.

[3] W. Huﬀman and V. Pless, “Fundamentals of Error-Correcting Codes”, Cambridge

University Press, 2003.

4



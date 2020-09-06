# software-assignment





*A Human Study of Comprehension and Code Summarization*

Paper-1
Summary-1

Software developers spend a great deal of time reading and understanding code that is poorly-documented, written by other developers, or developed using differing styles.
 During the past decade, researchers have investigated techniques for automatically documenting code to improve comprehensibility.
 In particular, recent advances in deep learning have led to sophisticated summary generation techniques that convert functions or methods to simple English strings that succinctly describe that code’s behavior. 
However, automatic summarization techniques are assessed using internal metrics such as BLEU scores, which measure natural language properties in translational models, or ROUGE scores, which measure overlap with human-written text.
 Unfortunately, these metrics do not necessarily capture how machine-generated code summaries actually affect human comprehension or developer productivity. We conducted a human study involving both university students and professional developers (n = 45). 
Participants reviewed Java methods and summaries and answered established program comprehension questions. In addition, participants completed coding tasks given summaries as specifications. 
Critically, the experiment controlled the source of the summaries: for a given method, some participants were shown human-written text and some were shown machine-generated text. We found that participants performed significantly better (p = 0.029) using human-written summaries versus machine-generated summaries. 
However, we found no evidence to support that participants perceive human- and machine-generated summaries to have different qualities. In addition, participants’ performance showed no correlation with the BLEU and ROUGE scores often used to assess the quality of machine-generated summaries.
 These results suggest a need for revised metrics to assess and guide automatic summarization techniques.




*A Soft Alignment Model for Bug Deduplication*

Paper-2
Summary-2

In this section, we describe our proposed Soft Alignment Model for
Bug Deduplication (SABD). This model receives a pair of bug reports:
a new query report q and a candidate reportc previously submitted
to the repository. The model outputs the probability P(y|q,c) of q
being a duplicate of c, where y indicates whether the given reports
are duplicate (y = 1) or not (y = 0). We consider a bug report to
be composed of the categorical fields, a summary and a descrip-
tion. Given a query report q, the values of its categorical fields are
represented as the tuple q
cat while the sequence of words of its
summary and description are denoted as q
s
and q
d
, respectively.
The same notation is employed for the candidate c.
Figure 1 depicts the SABD architecture. As we can see, SABD is
composed of the categorical and textual modules (two sub-networks)
that independently compare the categorical and textual data from
both reports, respectively. The classifier receives these module
outputs and produces the final prediction P(y|q,c). While the cate-
gorical module is a straightforward dense neural network, a more
sophisticated architecture is employed by the textual module to
handle text. The core of this module is the soft alignment comparison
layer that allows the model to dynamically access distinct infor-
mation from the text. This mechanism is expected to improve the
model capacity to focus on relevant features in the textual data
for the deduplication. In the remainder, we describe the details of
SABD and its modules.




*Relocatable Addressing Model for Symbolic Execution*

Paper-3
Summary-3
Model
We propose a new addressing model, where the address of an object
is a symbolic value, rather than a concrete one. As before, the pro-
gram’s address space is represented using a set of memory objects:
mo = (α,size, arr) ∈ 2
E×N
+×A
.
However, the base address of an object is now a symbolic value
α ∈ E and not a concrete one. We enforce the non-overlapping
property of different objects using hidden concrete base addresses:
Whenever the program allocates a memory object, we create an
address pair which consists of two values: a symbolic one α and a
concrete value c. The concrete value c is used to ensure that the
allocated objects do not overlap in the same way that is done in the
existing model. The symbolic value α is the value that propagates
to the symbolic state.
We maintain the correlation between the symbolic addresses and
the concrete ones using address constraints (AC). These constraints,
which are distinct from the path constraints of the symbolic state,
record equalities of the form:
α = e
where e is an expression over the hidden concrete addresses and
the symbolic ones.
Note that the address constraints are not part of the path con-
straints, they are only used when we construct a query for the
solver. Under this model, the address expressions stored in the sym-
bolic state are symbolic, and any other expression might depend on
these symbolic values, which are not constrained under the path
constraints. Therefore, we substitute the address constraints before
passing an expression e to the solver, that is: e[αi /ei] (for each
address constraint αi = ei
).
Remark. Another way to achieve the non-overlapping property
is to extend the path constraints of the symbolic state with appro-
priate constraints regarding the values of the base addresses. If we
have memory objects (α1,size1, arr1), ..., (αn,sizen, arrn ), then we
could have used the following constraints:
∀i , j. [αi
, αi + sizei
) ∩ [αj
, αj + sizej
) = ∅.
However, we found this approach not scalable, as it adds additional
constraints and symbolic values (depending on the number of ob-
jects in the symbolic state), making constraint solving significantly
harder.
To illustrate our new addressing model, consider the program
from Figure 2. When the array of pointers is allocated at line 2, we
do the following: Assuming that a pointer size is 8 bytes, we first
create a new memory object mo1 = (α1, 16, arr1) with an address
pair (α1,c1), and add mo1 to the address space. Then, we add a new
address constraint α1 = c1, and the symbolic value α1 is assigned to
be the value of the local variable array.





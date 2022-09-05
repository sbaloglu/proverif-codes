# proverif-codes

According to the paper "Election Verifiability in Receipt-free Voting Protocols" 
by Sevdenur Baloglu, Sergiu Bursuc, Sjouke Mauw, Jun Pang; 

for end-to-end (E2E) election verifiability regarding iv_\circ, iv_\bullet, res_\circ, and res_\bullet, 
we check the following queries in the ProVerif codes:

- E2E[iv_\circ, res_\circ] : queries WIV1, WIV2, WIV3, ELI, RES2, REG1, REG2, LINK1, LINK2, ONE
- E2E[iv_\bullet, res_\circ] : queries IV1, IV2, IV3, ELI, RES2, REG1, REG2, LINK1, LINK2, ONE
- E2E[iv_\circ, res_\bullet] : queries WIV1, WIV2, WIV3, ELI, RES1, REG1, REG2, LINK1, LINK2, ONE
- E2E[iv_\bullet, res_\bullet] : queries WIV1, WIV2, WIV3, ELI, RES1, REG1, REG2, LINK1, LINK2, ONE

for an adversary model (A1-A7) labeled in the name of code. For example, belenios-a1.pv is the ProVerif code
for the adversary model A1. Similarly, selene-a1.pv represents the adversary model A1' according to the paper. 

WIVi is the query regarding only for honest voters, whereas IVi is the one general for both honest and corrupted 
voters for i=1,2,3. 

RES1 represents strong E2E verifiability with res_\bullet, whereas RES2 represents weak E2E verifiability 
with res_\circ. 

For the Hyperion codes for A2, A3, A4, A5 and A6,  we check iv_\circ by defining an event Honest(id) 
and adding the following restriction:

restriction id: bitstring;
            event(Honest(id)) && event(Corrupted(id)) ==> false.
            
This allows us to terminate the queries for honest voters in different files hyperion-ai-iv-circ.pv for i=2,3,4,5,6. 

Moreover, we check iv_\bullet regarding corrupted voters for some queries since the others cause 
non-termination issue. However, in the files hyperion-ai-iv-bullet.pv for i=2,3,4,5,6,  
the falsifications on queries show the attacks on corrupted voters violating E2E verifiability. 




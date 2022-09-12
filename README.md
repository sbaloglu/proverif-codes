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

In the SeleneRF code for the adversary model A2, IV2 does not terminate (it was run about 54 hours). 
There are also termination issues with IV1, IV2, and RES2 for the Hyperion code for adversary model A3. 
For those two, we check iv_\circ by defining an event Honest(id) and adding the following restriction:

restriction id: bitstring;
            event(Honest(id)) && event(Corrupted(id)) ==> false.
            
This restriction allows us to terminate the queries for honest voters in additional files named with 
selene-rf-a2-iv-circ.pv and hyperion-a3-iv-circ.pv. 

Regarding corrupted voters, we provide the files selene-rf-a2-iv-bullet.pv and hyperion-a3-iv-bullet.pv 
to check iv_\bullet. The queries in those two, except the ones non-terminated, show the attacks 
on corrupted voters violating E2E verifiability. 




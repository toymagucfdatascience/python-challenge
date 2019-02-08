# python-challenge
Election Results
--------------------------
Total Votes:3521001
------------------------
Candidates Number of Votes Percentage Of Vote
s Khan   2218231                    63.00
 Correy  704200                     20.0%
Li       492940                     14.0%
O'Tooley 105630                     3.0%
---------------------------------------------
Winner:khan

PyPoll/pypoll_main.py
______________________________________________________
import os
import pandas as pd
import numpy as np

root_pat =os.path.join(os.getcwd(),".")
data_path = os.path.join(root_path, "raw_data")
output_path=os.path.join(root_path,"output")


filepaths=[
    for file in os.listdir(data_path):
    if file.endswith(".csv"):
    filepath.append(os.path.join(data_path,file))


for file in filepaths:
df = file
df_pd = pd.read_csv(df)

tot_votes = df_pd["candidates"].count()

cand_votes =df_pd["candidates"].value_counts()
cand_votes_df =pd.DataFrame(cand_votes)
cand_votes_df.colums=["votes"]

candidates_list =cand_votes_df.iloc[:,0].tolist()
vote_list = cand_votes_df.iloc[:,0].tolist()


percent_votes =((votes_list/tot_votes)*100).round(1)
percent_list=list(map("{}%".format, percent_votes))

results_df = pd.DataFrame({
    "candidate": candidate_list,
    "Number of votes": votes_list,
    "percentage of votes": percent_list


})

win_df =result_df.set_index( "number of votes")
win_votes = max(vote_list)
winner = win_df.loc[win_votes].Candidate

_, filename, _= filename.split(".csv")

ptint(
    f"Election Result -{filename}\n"
    f"--------------------------------------\n"
    f"Total Votes:{tot_votes}\n"
    f"---------------------------------------\n"
    f"{result_df.to_string(index=False)}\n"
    f"----------------------------------------\n"
    f"Winner: {winner}\n"
)0
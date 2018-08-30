import random;

# seq = [10];
# seq2 = [10];
# seq_n_users = [10, 100, 1000, 10000, 100000,1000000,10000000,100000000];
# seq_n_updates = [10, 100, 1000, 10000, 100000,1000000,10000000,100000000];
seq_mal_off = [1,2,3,4,5,6,7,8,9,10,11];
# seq_interest_rate = [x * 0.0001096 for x in seq_interest_rate]
# seq2 = [10, 100, 1000, 10000, 100000]
results=[];


for n_aux in seq_mal_off:
    # print "number of users: ",n_users;
    current_n_users = [];
    n_users = 1000; #say 1000 users per factory
    off = 0.0000001;#*n_aux; #prob of becoming unresponsive unlimitedly (per user)
    mal = 0.00000001;#*n_aux; #prob of behaving maliciously (per user)
    # say 1 tick = 1 minute, 24 hours to update channel, but updating takes 2 mins
    mal_factory = 1-((1-mal)**n_users) #sum (factory.users.mal); # (prob of at least one being malicious in n)
    off_factory = 1-((1-off)**n_users)#sum (factory.users.off); # (one being unresponsive in n)
    # for interest_rate in seq_interest_rate:
    n_updates=10000;
    n_factory = 1000; #say 1000 factories
    # print "number of updates: ",n_updates;
    current_n_updates = [];
    interest_rate = 0.0001096*n_aux; #4 per year. This implies that r = 4/365/100 = 0.0001096 per day. ("How to Charge Lihgtning")
    print "# users:",n_users,", mal:",mal,", off:",off,"n_updates:", n_updates,"n_factory:",n_factory,", interest_rate:",interest_rate;
    rand_mantissa = 10000.0;
    n_factory2=n_factory;
    res_average = [];
    for i in range (0,n_factory2): #for each factory
        j=1
        closed = False;
        while j<=n_updates and not closed:
            rand = random.randrange(0,rand_mantissa)/rand_mantissa;
            if(rand<off_factory+mal_factory or j==(n_updates-1)):#user unresponsive before updating -> can't update or last one
                #DMC
                # res= (interest_rate,j,interest_rate*(n_updates-j));
                #lightning 
                res =(interest_rate,j,interest_rate);
                current_n_updates.append(res);
                n_factory-=1#one factory less
                closed = True;
            j=j+1;
    current_n_users.append(current_n_updates);
    res_average.append([sum(y) / float(len(y)) for y in zip(*current_n_updates)]);
    res_average = res_average[0];
    print res_average[0],  res_average[1], res_average[2];
results.append(current_n_users);        

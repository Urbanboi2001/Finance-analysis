library(data.table)
library(ggplot2)
dt_in<-fread("C:/Users/Barun/Fin/Log.csv")
#----------------Preprocessing----------------

#Remove rows
dt_in<-dt_in[-(1:22),]


#Remove Columns
dt_in<-dt_in[,-3:-4]
dt_in<-dt_in[,-4]
dt_in<-dt_in[,-4]


#Rename Column
names(dt_in)<-c("Date","Transaction","Amount")


#Change amount type to numeric
dt_in$Amount<-as.numeric(as.character(dt_in$Amount))

#Change Transactions to lower case
dt_in[,Transaction:=tolower(Transaction)]

# Remove credit transactions
dt_in<-dt_in[Amount!=0]
dt_in<-dt_in[Amount!=38611]
dt_in<-dt_in[Transaction!=""]


sapply(dt_in, class)

#Transaction categorization
#Clothing
Cloth_key<-c("shoes","cloth","reliance tren")
Cloth_Key_patter<-paste(Cloth_key,collapse = "|")
dt_in[grepl(Cloth_Key_patter,Transaction), Category:="Clothing"]

#Medical
Medical_key<-c("medic","medical","medicine")
Medical_Key_patter<-paste(Medical_key,collapse = "|")
dt_in[grepl(Medical_Key_patter,Transaction), Category:="Medical"]

#Online Shopping
Online_key<-c("amazon","flipkart","myntra.")
Online_Key_patter<-paste(Online_key,collapse = "|")
dt_in[grepl(Online_Key_patter,Transaction), Category:="Online Shopping"]

#Car
car_key<-c("fuel","wash","indrajmull kurda","petrol","entel")
car_Key_patter<-paste(car_key,collapse = "|")
dt_in[grepl(car_Key_patter,Transaction), Category:="Car expenses"]

#food
food_key<-c("food","sweet","lasom dolma","cake","fruit","native","snack","party","rum","grocer")
food_Key_patter<-paste(food_key,collapse = "|")
dt_in[grepl(food_Key_patter,Transaction), Category:="food expenses"]

#Bills
Bill_key<-c("sikkimpnon","mobile","recharge")
Bill_Key_patter<-paste(Bill_key,collapse = "|")
dt_in[grepl(Bill_Key_patter,Transaction), Category:="Bills"]

#Investment
Inv_key<-c("indianclrcorpltd","nippon","njindia"," indian clearing")
Inv_Key_patter<-paste(Inv_key,collapse = "|")
dt_in[grepl(Inv_Key_patter,Transaction), Category:="Investment"]

#ATM Withdrawal
ATM_key<-c("atw")
ATM_Key_patter<-paste(ATM_key,collapse = "|")
dt_in[grepl(ATM_Key_patter,Transaction), Category:="ATM Withdrawal"]

fwrite(dt_in,"C:/Users/Barun/Fin/Output.csv")


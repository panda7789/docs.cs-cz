---
title: "System.Transactions – integrace s SQL serverem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 21924441c091c53a79d4b7bf8a683f8a7c74bd07
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="systemtransactions-integration-with-sql-server"></a>System.Transactions – integrace s SQL serverem
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Verze 2.0 zavedená rozhraní transakce, které je přístupné prostřednictvím <xref:System.Transactions> oboru názvů. Toto rozhraní zpřístupní transakce způsobem, který je v plně integrovaná [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], včetně [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 Kromě těchto vylepšení programovatelnosti <xref:System.Transactions> a [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] můžou spolupracovat a koordinovat optimalizace při práci s transakce. Je možné zvýšit transakce lightweight (místní) transakci, která bude automaticky povýšen na plně distribuovanou transakci na podle potřeby.  
  
 Počínaje [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> podporuje možné zvýšit transakce při práci s [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]. Možné zvýšit transakce nevyvolá přidaném starat se o distribuované transakce Pokud přidaném režie není nutné. Možné zvýšit transakce jsou automatické a nevyžadují žádný zásah od vývojáře.  
  
 Možné zvýšit transakce jsou k dispozici pouze při použití [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server (`SqlClient`) s [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].  
  
## <a name="creating-promotable-transactions"></a>Vytváření možné zvýšit transakcí  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider pro SQL Server poskytuje podporu pro možné zvýšit transakce, které jsou zpracovány prostřednictvím třídy v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> oboru názvů. Možné zvýšit transakce optimalizovat distribuované transakce odložit vytváření distribuované transakce, dokud nebude potřeba. Pokud jen jeden správce prostředků se vyžaduje, dojde k žádné distribuované transakce.  
  
> [!NOTE]
>  Ve scénáři částečně důvěryhodné <xref:System.Transactions.DistributedTransactionPermission> je požadován při transakci je povýšit na distribuovanou transakci.  
  
## <a name="promotable-transaction-scenarios"></a>Scénáře možné zvýšit transakce  
 Distribuované transakce obvykle využívají významné systémové prostředky, je spravováno nástrojem Microsoft Distributed Transaction Coordinator (MS DTC), která integruje všechny správce prostředků získat přístup v rámci transakce. Je možné zvýšit transakce speciální formu <xref:System.Transactions> transakci, která efektivně deleguje práce, kterou je jednoduchý [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] transakce. <xref:System.Transactions>, <xref:System.Data.SqlClient>, a [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] koordinaci pracovní zahrnuté ve zpracování transakcí, podle potřeby zvýšení jeho úrovně na úplné distribuovanou transakci.  
  
 Výhodou použití možné zvýšit transakcí je, že po otevření připojení pomocí aktivní <xref:System.Transactions.TransactionScope> transakce a žádná další připojení jsou otevřené, potvrzení transakce jako lightweight transakce, místo by docházelo k další Režijní náklady na úplné distribuované transakce.  
  
### <a name="connection-string-keywords"></a>Klíčová slova řetězec připojení  
 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Vlastnost podporuje klíčové slovo, `Enlist`, což znamená, zda <xref:System.Data.SqlClient> rozpozná transakční kontexty a automaticky zařazení připojení v distribuované transakci. Pokud `Enlist=true`, je připojení automaticky zařadit v aktuálním kontextu transakce otevírání vlákno. Pokud `Enlist=false`, `SqlClient` připojení nekomunikuje s distribuovanou transakci. Výchozí hodnota pro `Enlist` hodnotu true. Pokud `Enlist` není zadaný v připojovacím řetězci, toto připojení je automaticky uvedené v distribuované transakci, pokud se jeden detekuje po otevření připojení.  
  
 `Transaction Binding` Klíčová slova v <xref:System.Data.SqlClient.SqlConnection> připojovací řetězec řízení připojení přidružení zařazené `System.Transactions` transakce. Je také k dispozici prostřednictvím <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> vlastnost <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Následující tabulka popisuje možné hodnoty.  
  
|– Klíčové slovo|Popis|  
|-------------|-----------------|  
|Implicitní odpojení|Výchozí nastavení Připojení odpojí od transakce, až skončí, přepnutí zpět do režimu automatického zápisu režimu.|  
|Explicitní odpojení|Připojení zůstane připojený k transakci, dokud nezavře transakce. Připojení se nezdaří, pokud přidružené transakce není aktivní nebo neodpovídá <xref:System.Transactions.Transaction.Current%2A>.|  
  
## <a name="using-transactionscope"></a>Pomocí TransactionScope  
 <xref:System.Transactions.TransactionScope> Třída provede blok kódu transakční pomocí implicitně zapsání připojení v distribuované transakce. Je třeba zavolat <xref:System.Transactions.TransactionScope.Complete%2A> metoda na konci <xref:System.Transactions.TransactionScope> blok před zároveň je nechává. Opouštění bloku vyvolá <xref:System.Transactions.TransactionScope.Dispose%2A> metoda. Pokud byla vyvolána výjimka, že příčiny, které se považuje za kód, který nechte oboru, transakce zrušena.  
  
 Doporučujeme vám, že používáte `using` blok k Ujistěte se, že <xref:System.Transactions.TransactionScope.Dispose%2A> se volá na <xref:System.Transactions.TransactionScope> objekt při použití blokovat je byl ukončen. Selhání potvrzení nebo vrácení čekající transakce může výrazně poškodit výkon, protože výchozí časový limit pro <xref:System.Transactions.TransactionScope> je jedna minuta. Pokud nepoužijete `using` příkaz, je třeba provést všechny pracovní v `Try` blokovat a explicitně volání <xref:System.Transactions.TransactionScope.Dispose%2A> metoda v `Finally` bloku.  
  
 Pokud dojde k výjimce v <xref:System.Transactions.TransactionScope>, transakce je označena jako nekonzistentní a opuštění. Bude vrácena zpět, když <xref:System.Transactions.TransactionScope> je zrušen. Pokud dojde k žádná výjimka, potvrzení zúčastněných transakce.  
  
> [!NOTE]
>  `TransactionScope` Třída vytvoří transakce s <xref:System.Transactions.Transaction.IsolationLevel%2A> z `Serializable` ve výchozím nastavení. V závislosti na vaší aplikace můžete chtít zvažte snížení úrovně izolace, aby se zabránilo vysoké kolizí ve vaší aplikaci.  
  
> [!NOTE]
>  Doporučujeme provádět jenom aktualizace, vložení, a odstraní v rámci distribuované transakce, protože jejich spotřebovávat prostředky významné databáze. Příkazy SELECT může zbytečně zamknout databáze prostředků, a v některých scénářích možná budete muset použít transakce pro vybere. Všechny pracovní databáze by mělo být provedeno v oboru transakce, pokud se týká jiných správci zpracovaných prostředků. I když k výjimce v oboru transakce zabraňují transakce potvrzení, <xref:System.Transactions.TransactionScope> třídy nemá vybavení pro vrácení zpět všechny změny kódu udělal mimo obor vlastní transakce. Pokud máte určitou akci při transakce je vrácena zpět, je nutné napsat vlastní implementaci <xref:System.Transactions.IEnlistmentNotification> rozhraní a explicitně uvést v transakci.  
  
## <a name="example"></a>Příklad  
 Práce s <xref:System.Transactions> vyžaduje, abyste měli odkaz na System.Transactions.dll.  
  
 Následující funkce ukazuje, jak vytvořit možné zvýšit transakce proti dva různé instance systému SQL Server, reprezentována dva různé <xref:System.Data.SqlClient.SqlConnection> objekty, které jsou uzavřen do <xref:System.Transactions.TransactionScope> bloku. Kód vytvoří <xref:System.Transactions.TransactionScope> blokovat s `using` příkaz a otevře první připojení, které automaticky využívá ho <xref:System.Transactions.TransactionScope>. Transakce je původně uvedené jako lightweight transakce, není úplná distribuované transakce. Druhé připojení je v uvedené <xref:System.Transactions.TransactionScope> pouze v případě, že příkaz v prvním připojení nevyvolá výjimku. Po otevření druhé připojení transakce automaticky povýšen na úplné distribuovanou transakci. <xref:System.Transactions.TransactionScope.Complete%2A> Je volána metoda, která potvrdí transakce pouze v případě, že byly vyvolány žádné výjimky. Pokud byla vyvolána výjimka v libovolném bodě <xref:System.Transactions.TransactionScope> bloku `Complete` bude nebyla volána a bude distribuované transakce vrácení zpět, když <xref:System.Transactions.TransactionScope> je zveřejněn. na konci jeho `using` bloku.  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can   
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the   
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2   
                // only when there is a chance that the transaction can commit.     
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not   
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can   
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the   
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2   
                ' only when there is a chance that the transaction can commit.     
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will   
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a>Viz také  
 [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

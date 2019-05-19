---
title: Integrace System.Transactions s SQL Serverem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 09fcf3f1a7e58a4bd8c2c6b0d25c24f32ea5ec5e
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880584"
---
# <a name="systemtransactions-integration-with-sql-server"></a>Integrace System.Transactions s SQL Serverem
Rozhraní .NET Framework verze 2.0 zavedená, který je přístupný prostřednictvím rozhraní transakce <xref:System.Transactions> oboru názvů. Toto rozhraní poskytuje transakce způsobem, který je plně integrováno v rozhraní .NET Framework, ADO.NET.  
  
 Kromě vylepšení programovatelnosti <xref:System.Transactions> a ADO.NET můžou spolupracovat a koordinovat optimalizace při práci s transakcí. Možné zařazení transakce je zjednodušené transakce (místní), která bude automaticky povýšen na plně distribuované transakce podle potřeby.  
  
 Od verze ADO.NET 2.0 <xref:System.Data.SqlClient> podporuje možné zařazení transakce při práci se serverem SQL Server. Možné zařazení transakce vyvolat není přidaný režie distribuované transakce, pokud přidaného zatížení je povinný. Možné zařazení transakce jsou automatické a vyžadují bez nutnosti zásahu od vývojáře.  
  
 Možné zařazení transakce jsou k dispozici pouze při použití zprostředkovatele dat .NET Framework pro SQL Server (`SqlClient`) se systémem SQL Server.  
  
## <a name="creating-promotable-transactions"></a>Vytváření možné zařazení transakce  
 Zprostředkovatele .NET Framework pro SQL Server poskytuje podporu pro možné zařazení transakce, které jsou zpracovány prostřednictvím třídy v rozhraní .NET Framework <xref:System.Transactions> oboru názvů. Možné zařazení transakce odložené vytváření distribuovaných transakcí, dokud je potřeba optimalizovat distribuované transakce. Pokud pouze jedna resource manager je potřeba, dojde k žádné distribuované transakce.  
  
> [!NOTE]
>  Ve scénáři částečně důvěryhodné <xref:System.Transactions.DistributedTransactionPermission> se vyžaduje při povýšení transakce na distribuovanou transakci.  
  
## <a name="promotable-transaction-scenarios"></a>Možné zařazení transakce scénáře  
 Distribuované transakce obvykle spotřebovat významné systémových prostředků spravuje Microsoft Distributed Transaction Coordinator (MS DTC), která integruje všechny správce prostředků přistupovat v transakci. Možné zařazení transakce je zvláštní forma <xref:System.Transactions> transakce, která efektivně deleguje práce, kterou jednoduché transakce systému SQL Server. <xref:System.Transactions>, <xref:System.Data.SqlClient>, a SQL Server koordinovat činnost zahrnuté ve zpracování transakcí, zvýšení jeho úrovně je úplná distribuované transakce podle potřeby.  
  
 Výhodou použití možné zařazení transakce je, že při otevření připojení pomocí aktivní <xref:System.Transactions.TransactionScope> transakce a žádná další připojení jsou otevřené, potvrzení transakcí jako jednoduchý transakce, místo něho další režie úplná distribuované transakce.  
  
### <a name="connection-string-keywords"></a>Klíčová slova připojovací řetězec  
 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Vlastnost podporuje klíčového slova `Enlist`, což znamená, zda <xref:System.Data.SqlClient> zjistí Transakční kontextu a automaticky zařazení připojení v distribuované transakci. Pokud `Enlist=true`, připojení se automaticky uveden v otevírání vlákno aktuální kontext transakce. Pokud `Enlist=false`, `SqlClient` připojení nekomunikuje s distribuovanou transakci. Výchozí hodnota pro `Enlist` má hodnotu true. Pokud `Enlist` není zadaná v připojovacím řetězci připojení automaticky zařazena v distribuované transakci je-li jeden zjištěna při otevření připojení.  
  
 `Transaction Binding` Klíčových slov v <xref:System.Data.SqlClient.SqlConnection> připojovací řetězec řízení připojení k přidružení zařazených `System.Transactions` transakce. Je také k dispozici prostřednictvím <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> vlastnost <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Následující tabulka popisuje možné hodnoty.  
  
|Klíčové slovo|Popis|  
|-------------|-----------------|  
|Implicitní zrušení vazby|Výchozí nastavení Připojení se odpojí od transakce při ukončení, přepnete zpět do režimu automatický zápis.|  
|Explicitní odpojení|Připojení zůstane připojený k transakci, dokud není zavřena transakce. Připojení se nezdaří, pokud přidružené transakce není aktivní nebo se neshoduje s <xref:System.Transactions.Transaction.Current%2A>.|  
  
## <a name="using-transactionscope"></a>Pomocí objektu TransactionScope  
 <xref:System.Transactions.TransactionScope> Třída umožňuje blok kódu transakční pomocí implicitně zapsání připojení v distribuované transakci. Je třeba zavolat <xref:System.Transactions.TransactionScope.Complete%2A> metoda na konci <xref:System.Transactions.TransactionScope> blok před se v něm. Opuštění bloku volá <xref:System.Transactions.TransactionScope.Dispose%2A> metody. Pokud byla vyvolána výjimka, že příčiny, které se považuje za kód, který ponechte oboru transakce zrušena.  
  
 Doporučujeme používat `using` blok k Ujistěte se, že <xref:System.Transactions.TransactionScope.Dispose%2A> je volán na <xref:System.Transactions.TransactionScope> objektu na pomocí když je v bloku je byl ukončen. Selhání potvrzení nebo vrácení zpět čekajících transakce mohou výrazně poškodit výkonu, protože výchozí časový limit pro <xref:System.Transactions.TransactionScope> je jedna minuta. Pokud použijete `using` příkaz, je nutné provést veškerou práci v `Try` blokovat a explicitně volat <xref:System.Transactions.TransactionScope.Dispose%2A> metoda ve `Finally` bloku.  
  
 Pokud dojde k výjimce v <xref:System.Transactions.TransactionScope>, transakce je označena jako nekonzistentní a opuštění. Bude vrácena zpět, když <xref:System.Transactions.TransactionScope> je uvolněn. Pokud dojde k žádné výjimce, potvrzení zúčastněných transakce.  
  
> [!NOTE]
>  `TransactionScope` Třída vytvoří transakce s <xref:System.Transactions.Transaction.IsolationLevel%2A> z `Serializable` ve výchozím nastavení. V závislosti na vaší aplikaci můžete chtít zvážit snížení úrovně izolace, aby se zabránilo vysoké kolize ve vaší aplikaci.  
  
> [!NOTE]
>  Doporučujeme provádět jenom aktualizace, vložení, a odstraní v distribuované transakce, protože mohou spotřebovat významné databázových prostředků. Příkazy SELECT může zbytečně zamknout databázových prostředků, a v některých případech bude pravděpodobně nutné použít transakce pro vybere. Veškerá práce bez databáze má počítat mimo obor transakce, pokud zahrnuje další správci prostředků transakčního. I když výjimku v oboru transakce zabraňují transakce potvrzení, <xref:System.Transactions.TransactionScope> třída nemá žádné ustanovení pro vrácení zpět všechny změny kódu provedl nad rámec vlastní transakce. Pokud budete muset provést některé akce, když transakce je vrácena zpět, je nutné napsat vlastní implementaci <xref:System.Transactions.IEnlistmentNotification> rozhraní a explicitně uvést v transakci.  
  
## <a name="example"></a>Příklad  
 Práce s <xref:System.Transactions> vyžaduje, abyste měli odkaz na System.Transactions.dll.  
  
 Následující funkce ukazuje, jak vytvořit možné zařazení transakce na dvou různých instancích systému SQL Server, reprezentovány ve dvou různých <xref:System.Data.SqlClient.SqlConnection> objekty, které jsou obaleny <xref:System.Transactions.TransactionScope> bloku. Kód vytvoří <xref:System.Transactions.TransactionScope> blokovat s `using` příkazu a otevře první připojení, které automaticky využívá ho <xref:System.Transactions.TransactionScope>. Transakce je původně zapsán jako jednoduchý transakce, není úplná distribuované transakce. Druhé připojení je uveden v <xref:System.Transactions.TransactionScope> pouze v případě, že příkaz v prvním připojení nevyvolá výjimku. Po otevření druhé připojení transakce je automaticky povýšen na úplná distribuované transakce. <xref:System.Transactions.TransactionScope.Complete%2A> Je vyvolána metoda, která potvrzení transakce, pouze v případě, že máte nebyly vytvořeny žádné výjimky. Pokud byla vyvolána výjimka v libovolném bodě <xref:System.Transactions.TransactionScope> bloku `Complete` se nebude volat a distribuované transakce se vrátit zpět, když <xref:System.Transactions.TransactionScope> je uvolněna na konci jeho `using` bloku.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

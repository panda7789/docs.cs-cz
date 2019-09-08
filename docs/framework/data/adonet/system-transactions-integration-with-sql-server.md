---
title: Integrace System.Transactions s SQL Serverem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 075eea42c65a822fc46ca14f820599567c35d231
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791362"
---
# <a name="systemtransactions-integration-with-sql-server"></a>Integrace System.Transactions s SQL Serverem
.NET Framework verze 2,0 představila transakční rozhraní, ke kterému lze přistupovat <xref:System.Transactions> prostřednictvím oboru názvů. Toto rozhraní zpřístupňuje transakce způsobem, který je plně integrovaný do .NET Framework, včetně ADO.NET.  
  
 Kromě vylepšení <xref:System.Transactions> programovatelnosti a ADO.NET můžou při práci s transakcemi spolupracovat při koordinaci optimalizací. Transakce promoící je odlehčená (místní) transakce, kterou lze automaticky zvýšit na plně distribuovanou transakci podle potřeby.  
  
 Počínaje verzí ADO.NET 2,0 <xref:System.Data.SqlClient> podporuje transakce promoící při práci s SQL Server. Transakce promoící nevyvolává přidanou režii distribuované transakce, pokud není nutná přidaná režie. Transakce s propagačními akcemi jsou automatické a od vývojářů nevyžadují žádný zásah.  
  
 Transakce s přístupnými transakcemi jsou k dispozici, pouze pokud používáte`SqlClient`.NET Framework Zprostředkovatel dat pro SQL Server () s SQL Server.  
  
## <a name="creating-promotable-transactions"></a>Vytváření transakcí promoce  
 Poskytovatel .NET Framework pro SQL Server poskytuje podporu pro transakce, které jsou zpracovávány prostřednictvím tříd v oboru názvů .NET Framework <xref:System.Transactions> . Transakce Promote optimalizuje distribuované transakce odložením vytvoření distribuované transakce, dokud ji nepotřebujete. Pokud je vyžadován pouze jeden správce prostředků, neprobíhá žádná distribuovaná transakce.  
  
> [!NOTE]
> V částečně důvěryhodném scénáři <xref:System.Transactions.DistributedTransactionPermission> je vyžadován při povýšení transakce na distribuovanou transakci.  
  
## <a name="promotable-transaction-scenarios"></a>Scénáře transakcí s možností použití  
 Distribuované transakce obvykle využívají významné systémové prostředky spravované službou Microsoft DTC (Distributed Transaction Coordinator) (MS DTC), která integruje všechny správce prostředků, ke kterým se přistupovalo v transakci. Transakce typu promoe je speciální forma <xref:System.Transactions> transakce, která efektivně deleguje práci do jednoduché transakce SQL Server. <xref:System.Transactions>, <xref:System.Data.SqlClient>a SQL Server koordinovat práci, která je zapojená do zpracování transakce, a podle potřeby ji propagovat na úplnou distribuovanou transakci.  
  
 Výhodou použití transakcí s více instancemi je, že když je připojení otevřeno pomocí aktivní <xref:System.Transactions.TransactionScope> transakce a žádné jiné připojení není otevřeno, transakce je považována za odlehčenou transakci místo toho, aby vyplatila další Režie plné distribuované transakce.  
  
### <a name="connection-string-keywords"></a>Klíčová slova připojovacího řetězce  
 Vlastnost podporuje klíčové slovo, které označuje, zda <xref:System.Data.SqlClient> bude detekovat transakční kontexty a automaticky zařadit připojení v distribuované transakci. `Enlist` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Pokud `Enlist=true`se připojení automaticky zařadí do kontextu aktuálního transakce otevřeného vlákna. Pokud `Enlist=false`připojenínekomunikuje sdistribuovanoutransakcí.`SqlClient` Výchozí hodnota pro `Enlist` je true. Pokud `Enlist` není zadán v připojovacím řetězci, připojení je automaticky zařazeno do distribuované transakce, pokud je zjištěno při otevření připojení.  
  
 Klíčová slova <xref:System.Data.SqlClient.SqlConnection> v připojovacím řetězci řídí `System.Transactions` přidružení připojení k zařazené transakci. `Transaction Binding` Je také k dispozici prostřednictvím <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> vlastnosti. <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
 Následující tabulka popisuje možné hodnoty.  
  
|Klíčové slovo|Popis|  
|-------------|-----------------|  
|Implicitní zrušení vazby|Výchozí nastavení Připojení se odpojí z transakce, když skončí, a přepne zpět do režimu autocommit.|  
|Explicitní zrušení vazby|Připojení zůstane připojené k transakci, dokud transakce není uzavřená. Pokud není přidružená transakce aktivní nebo se neshoduje <xref:System.Transactions.Transaction.Current%2A>, připojení se nezdaří.|  
  
## <a name="using-transactionscope"></a>Použití TransactionScope  
 <xref:System.Transactions.TransactionScope> Třída vytváří transakční blok kódu implicitně zařazováním připojení v distribuované transakci. Před zavoláním <xref:System.Transactions.TransactionScope.Complete%2A> metody je nutné volat metodu na <xref:System.Transactions.TransactionScope> konci bloku. Ukončení bloku vyvolá <xref:System.Transactions.TransactionScope.Dispose%2A> metodu. Pokud byla vyvolána výjimka, která způsobí, že kód opustí rozsah, transakce je považována za přerušenou.  
  
 Doporučujeme, abyste pomocí `using` bloku zajistili, že <xref:System.Transactions.TransactionScope.Dispose%2A> se zavolá na <xref:System.Transactions.TransactionScope> objekt při ukončení bloku using. Nepovedlo se zapsat nebo vrátit zpět nevyřízené transakce může významně poškodit výkon, protože výchozí časový limit <xref:System.Transactions.TransactionScope> je 1 minuta. Pokud nepoužijete `using` příkaz, musíte provést veškerou práci `Try` v <xref:System.Transactions.TransactionScope.Dispose%2A> bloku a explicitně `Finally` volat metodu v bloku.  
  
 Pokud dojde k výjimce v <xref:System.Transactions.TransactionScope>, transakce je označena jako nekonzistentní a je opuštěna. Bude vrácena zpět, jakmile <xref:System.Transactions.TransactionScope> bude uvolněna. Pokud nedojde k žádné výjimce, připustí se účastnící se transakce.  
  
> [!NOTE]
> Třída vytvoří `Serializable` ve výchozím nastavení transakci s <xref:System.Transactions.Transaction.IsolationLevel%2A>hodnotou. `TransactionScope` V závislosti na vaší aplikaci můžete zvážit snížení úrovně izolace, abyste se vyhnuli vysokému kolizí ve vaší aplikaci.  
  
> [!NOTE]
> Doporučujeme, abyste v rámci distribuovaných transakcí prováděli pouze aktualizace, vkládání a odstraňování, protože využívají významné databázové prostředky. Příkazy SELECT můžou nenutně uzamknout databázové prostředky a v některých scénářích může být nutné použít transakce pro výběr. Jakákoli nedatabázová práce by se měla provádět mimo rozsah transakce, pokud nezahrnuje další správce prostředků s podporou transakcí. I když výjimka v oboru transakce brání v potvrzení transakce, třída nemá žádné zřízení pro vrácení <xref:System.Transactions.TransactionScope> zpět všech změn, které kód provedl mimo rozsah samotné transakce. Pokud je nutné provést určitou akci při vrácení transakce zpět, musíte napsat vlastní implementaci <xref:System.Transactions.IEnlistmentNotification> rozhraní a explicitně uvést do transakce.  
  
## <a name="example"></a>Příklad  
 Práce s <xref:System.Transactions> vyžaduje odkaz na System. Transactions. dll.  
  
 Následující funkce ukazuje, jak vytvořit transakci typu promoce na dvou různých instancích SQL Server reprezentovaných dvěma různými <xref:System.Data.SqlClient.SqlConnection> objekty, které jsou zabaleny <xref:System.Transactions.TransactionScope> do bloku. Kód vytvoří <xref:System.Transactions.TransactionScope> blok `using` s příkazem a otevře první připojení, které je automaticky <xref:System.Transactions.TransactionScope>zařadí do. Transakce je zpočátku zařazena jako odlehčená transakce, nikoli plná distribuovaná transakce. Druhé připojení je zařazeno <xref:System.Transactions.TransactionScope> pouze v případě, že příkaz v prvním připojení nevyvolá výjimku. Když je otevřeno druhé připojení, transakce je automaticky povýšena na úplnou distribuovanou transakci. <xref:System.Transactions.TransactionScope.Complete%2A> Metoda je vyvolána, která provádí transakci pouze v případě, že nebyly vyvolány žádné výjimky. Pokud byla výjimka vyvolána <xref:System.Transactions.TransactionScope> v jakémkoli bodě bloku, `Complete` nebude volána a distribuovaná transakce <xref:System.Transactions.TransactionScope> bude vrácena zpět, když je uvolněna na konci svého `using` bloku.  
  
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

- [Transakce a souběžnost](transactions-and-concurrency.md)
- [Přehled ADO.NET](ado-net-overview.md)

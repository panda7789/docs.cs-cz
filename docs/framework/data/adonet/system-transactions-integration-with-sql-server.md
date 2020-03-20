---
title: Integrace System.Transactions s SQL Serverem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 42007dafbdc9f61b9fc0776e0aaa2987551b704a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174235"
---
# <a name="systemtransactions-integration-with-sql-server"></a>Integrace System.Transactions s SQL Serverem
Rozhraní .NET Framework verze 2.0 zavedlo transakční architekturu, ke které lze přistupovat prostřednictvím oboru <xref:System.Transactions> názvů. Tento rámec zveřejňuje transakce způsobem, který je plně integrován v rozhraní .NET Framework, včetně ADO.NET.  
  
 Kromě vylepšení programovatelnosti <xref:System.Transactions> a ADO.NET mohou spolupracovat na koordinaci optimalizací při práci s transakcemi. Promotable transakce je lehký (místní) transakce, která může být automaticky povýšen na plně distribuované transakce podle potřeby.  
  
 Počínaje ADO.NET 2.0 <xref:System.Data.SqlClient> podporuje promotable transakce při práci s SQL Server. Promotable transakce nevyvolá přidané režie distribuované transakce, pokud je požadováno přidané režie. Promotable transakce jsou automatické a nevyžadují žádný zásah od vývojáře.  
  
 Promotable transakce jsou k dispozici pouze v případě, že`SqlClient`používáte zprostředkovatele dat rozhraní .NET Framework pro SQL Server ( ) s SQL Server.  
  
## <a name="creating-promotable-transactions"></a>Vytváření promotable transakcí  
 Zprostředkovatel rozhraní .NET Framework pro SQL Server poskytuje podporu pro promotable transakce, <xref:System.Transactions> které jsou zpracovány prostřednictvím tříd v oboru názvů rozhraní .NET Framework. Promotable transakce optimalizovat distribuované transakce odložením vytvoření distribuované transakce, dokud je potřeba. Pokud je vyžadován pouze jeden správce prostředků, nedojde k žádné distribuované transakci.  
  
> [!NOTE]
> V částečně důvěryhodném <xref:System.Transactions.DistributedTransactionPermission> scénáři je vyžadováno při povýšení transakce na distribuovanou transakci.  
  
## <a name="promotable-transaction-scenarios"></a>Scénáře promotable transakcí  
 Distribuované transakce obvykle spotřebovávají významné systémové prostředky spravované koordinátorem Microsoft Distributed Transaction Coordinator (MS DTC), který integruje všechny správce prostředků, ke kterým se v transakci přistupuje. Promotable transakce je zvláštní forma <xref:System.Transactions> transakce, která účinně deleguje práci na jednoduchou transakci SQL Server. <xref:System.Transactions>, <xref:System.Data.SqlClient>a SQL Server koordinovat práci spojenou se zpracováním transakce a podle potřeby ji povýšit na celou distribuovanou transakci.  
  
 Výhodou použití promotable transakce je, že při otevření připojení <xref:System.Transactions.TransactionScope> pomocí aktivní transakce a žádná další připojení jsou otevřeny, transakce potvrdí jako zjednodušené transakce, namísto vzniku další režii úplné distribuované transakce.  
  
### <a name="connection-string-keywords"></a>Klíčová slova připojovacího řetězce  
 Vlastnost <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> podporuje klíčové `Enlist`slovo , <xref:System.Data.SqlClient> které označuje, zda bude detekovat transakční kontexty a automaticky zařadit připojení v distribuované transakce. Pokud `Enlist=true`je připojení automaticky zapsáno v aktuálním kontextu transakce v počátečním vlákně. Pokud `Enlist=false` `SqlClient` připojení nespolupracuje s distribuovanou transakcí. Výchozí hodnota `Enlist` pro je true. Pokud `Enlist` není zadán v připojovacím řetězci, připojení je automaticky zapsáno do distribuované transakce, pokud je při otevření připojení rozpoznáno.  
  
 Klíčová `Transaction Binding` slova v <xref:System.Data.SqlClient.SqlConnection> připojovacím řetězci řídí `System.Transactions` přidružení připojení k zapisované transakci. Je také k <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> dispozici prostřednictvím nemovitosti <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Následující tabulka popisuje možné hodnoty.  
  
|Klíčové slovo|Popis|  
|-------------|-----------------|  
|Implicitní zrušení vazby|Výchozí nastavení Připojení se odpojí od transakce po jeho ukončení a přepne zpět do režimu automatického potvrzení.|  
|Explicitní zrušení vazby|Připojení zůstane připojeno k transakci, dokud není transakce uzavřena. Připojení se nezdaří, pokud přidružená transakce <xref:System.Transactions.Transaction.Current%2A>není aktivní nebo neodpovídá .|  
  
## <a name="using-transactionscope"></a>Použití oboru transakcí  
 Třída <xref:System.Transactions.TransactionScope> provede blok kódu transakční implicitně zapisovat připojení v distribuované transakci. Před opuštěním <xref:System.Transactions.TransactionScope.Complete%2A> <xref:System.Transactions.TransactionScope> je nutné volat metodu na konci bloku. Opuštění bloku vyvolá <xref:System.Transactions.TransactionScope.Dispose%2A> metodu. Pokud byla vyvolána výjimka, která způsobí, že kód opustit obor, transakce je považována za přerušeno.  
  
 Doporučujeme použít `using` blok a ujistěte <xref:System.Transactions.TransactionScope.Dispose%2A> se, <xref:System.Transactions.TransactionScope> že je volána na objekt při ukončení using bloku. Selhání potvrzení nebo vrácení zpět čekající transakce může výrazně poškodit výkon, protože výchozí časový limit pro je jedna minuta. <xref:System.Transactions.TransactionScope> Pokud nepoužijete `using` příkaz, musíte provést veškerou `Try` práci v <xref:System.Transactions.TransactionScope.Dispose%2A> bloku a `Finally` explicitně volat metodu v bloku.  
  
 Pokud dojde k výjimce <xref:System.Transactions.TransactionScope>v , transakce je označena jako nekonzistentní a je opuštěná. Bude vrácena zpět, <xref:System.Transactions.TransactionScope> když je vyřazen. Pokud nedojde k žádné výjimce, zúčastněné transakce potvrdí.  
  
> [!NOTE]
> Třída `TransactionScope` vytvoří transakci s <xref:System.Transactions.Transaction.IsolationLevel%2A> `Serializable` standardně. V závislosti na vaší aplikaci můžete zvážit snížení úrovně izolace, abyste se vyhnuli vysokým konfliktům ve vaší aplikaci.  
  
> [!NOTE]
> Doporučujeme provádět pouze aktualizace, vloží a odstraní v rámci distribuovaných transakcí, protože spotřebovávají významné databázové prostředky. Příkazy Select mohou zbytečně uzamknout databázové prostředky a v některých scénářích může být nutné použít transakce pro výběry. Všechny práce mimo databázi by měla být provedena mimo rozsah transakce, pokud zahrnuje jiné transakční správce prostředků. Přestože výjimka v rozsahu transakce brání transakce potvrzení, <xref:System.Transactions.TransactionScope> třída nemá žádné ustanovení pro vrácení zpět všechny změny, které váš kód provedl mimo rozsah samotné transakce. Pokud máte provést nějakou akci při transakce je vrácena zpět, <xref:System.Transactions.IEnlistmentNotification> je nutné napsat vlastní implementaci rozhraní a explicitně zařadit do transakce.  
  
## <a name="example"></a>Příklad  
 Práce <xref:System.Transactions> s vyžaduje, abyste měli odkaz na System.Transactions.dll.  
  
 Následující funkce ukazuje, jak vytvořit promotable transakce proti dvěma různými instancemi SERVERU SQL, reprezentované dvěma různými <xref:System.Data.SqlClient.SqlConnection> objekty, které jsou zabaleny do <xref:System.Transactions.TransactionScope> bloku. Kód vytvoří <xref:System.Transactions.TransactionScope> blok s `using` příkazem a otevře první připojení, které <xref:System.Transactions.TransactionScope>jej automaticky zařadí do . Transakce je zpočátku zapsána jako zjednodušená transakce, nikoli jako úplná distribuovaná transakce. Druhé připojení je zapsán <xref:System.Transactions.TransactionScope> a pouze v případě, že příkaz v prvním připojení nevyvolá výjimku. Při otevření druhého připojení je transakce automaticky povýšena na úplnou distribuovanou transakci. Metoda <xref:System.Transactions.TransactionScope.Complete%2A> je vyvolána, která potvrdí transakci pouze v případě, že nebyly vyvolány žádné výjimky. Pokud byla vyvolána výjimka v <xref:System.Transactions.TransactionScope> libovolném `Complete` bodě v bloku, nebude volána a <xref:System.Transactions.TransactionScope> distribuovaná transakce `using` se vrátí zpět, jakmile je uvolněn na konci jeho bloku.  
  
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

- [Transakce a souběžnost](transactions-and-concurrency.md)
- [Přehled ADO.NET](ado-net-overview.md)

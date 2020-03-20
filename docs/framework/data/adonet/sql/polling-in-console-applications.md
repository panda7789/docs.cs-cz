---
title: Dotazování v konzolových aplikacích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4ff084d5-5956-4db1-8e18-c5a66b000882
ms.openlocfilehash: 0cefca33bde94855a2bb20a6404dfd4e75a954c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174521"
---
# <a name="polling-in-console-applications"></a><span data-ttu-id="10016-102">Dotazování v konzolových aplikacích</span><span class="sxs-lookup"><span data-stu-id="10016-102">Polling in Console Applications</span></span>
<span data-ttu-id="10016-103">Asynchronní operace v ADO.NET umožňují zahájit časově náročné databázové operace v jednom vlákně při provádění jiných úloh v jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="10016-103">Asynchronous operations in ADO.NET allow you to initiate time-consuming database operations on one thread while performing other tasks on another thread.</span></span> <span data-ttu-id="10016-104">Ve většině scénářů však nakonec dosáhnete bodu, kdy by aplikace neměla pokračovat, dokud nebude dokončena operace databáze.</span><span class="sxs-lookup"><span data-stu-id="10016-104">In most scenarios, however, you will eventually reach a point where your application should not continue until the database operation is complete.</span></span> <span data-ttu-id="10016-105">V takových případech je užitečné dotazování asynchronní operace k určení, zda byla operace dokončena nebo ne.</span><span class="sxs-lookup"><span data-stu-id="10016-105">For such cases, it is useful to poll the asynchronous operation to determine whether the operation has completed or not.</span></span>  
  
 <span data-ttu-id="10016-106"><xref:System.IAsyncResult.IsCompleted%2A> Vlastnost můžete použít k tomu, abyste zjistili, zda byla operace dokončena.</span><span class="sxs-lookup"><span data-stu-id="10016-106">You can use the <xref:System.IAsyncResult.IsCompleted%2A> property to find out whether or not the operation has completed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10016-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="10016-107">Example</span></span>  
 <span data-ttu-id="10016-108">Následující konzolová aplikace aktualizuje data v ukázkové databázi **AdventureWorks** a provádí svou práci asynchronně.</span><span class="sxs-lookup"><span data-stu-id="10016-108">The following console application updates data within the **AdventureWorks** sample database, doing its work asynchronously.</span></span> <span data-ttu-id="10016-109">Chcete-li emulovat dlouhotrvající proces, v tomto příkladu vloží příkaz WAITWAIT do textu příkazu.</span><span class="sxs-lookup"><span data-stu-id="10016-109">In order to emulate a long-running process, this example inserts a WAITFOR statement in the command text.</span></span> <span data-ttu-id="10016-110">Za normálních okolností byste se nepokoušeli, aby vaše příkazy běžely pomaleji, ale v tomto případě je snazší demonstrovat asynchronní chování.</span><span class="sxs-lookup"><span data-stu-id="10016-110">Normally, you would not try to make your commands run slower, but doing so in this case makes it easier to demonstrate asynchronous behavior.</span></span>  
  
```vb  
Imports System  
Imports System.Data.SqlClient  
  
Module Module1  
  
    Sub Main()  
        ' The WAITFOR statement simply adds enough time to prove the
        ' asynchronous nature of the command.  
        Dim commandText As String = _  
         "UPDATE Production.Product " & _  
         "SET ReorderPoint = ReorderPoint + 1 " & _  
         "WHERE ReorderPoint Is Not Null;" & _  
         "WAITFOR DELAY '0:0:3';" & _  
         "UPDATE Production.Product " & _  
         "SET ReorderPoint = ReorderPoint - 1 " & _  
         "WHERE ReorderPoint Is Not Null"  
  
        RunCommandAsynchronously(commandText, GetConnectionString())  
  
        Console.WriteLine("Press Enter to continue.")  
        Console.ReadLine()  
    End Sub  
  
    Private Sub RunCommandAsynchronously( _  
     ByVal commandText As String, ByVal connectionString As String)  
  
        ' Given command text and connection string, asynchronously
        ' execute the specified command against the connection. For
        ' this example, the code displays an indicator as it's working,
        ' verifying the asynchronous behavior.
        Using connection As New SqlConnection(connectionString)  
            Try  
                Dim count As Integer = 0  
                Dim command As New SqlCommand(commandText, connection)  
                connection.Open()  
                Dim result As IAsyncResult = _  
                 command.BeginExecuteNonQuery()  
                While Not result.IsCompleted  
                    Console.WriteLine("Waiting ({0})", count)  
                    ' Wait for 1/10 second, so the counter  
                    ' doesn't consume all available resources
                    ' on the main thread.  
                    Threading.Thread.Sleep(100)  
                    count += 1  
                End While  
                Console.WriteLine( _  
                 "Command complete. Affected {0} rows.", _  
                 command.EndExecuteNonQuery(result))  
            Catch ex As SqlException  
                Console.WriteLine("Error ({0}): {1}", _  
                 ex.Number, ex.Message)  
            Catch ex As InvalidOperationException  
                Console.WriteLine("Error: {0}", ex.Message)  
            Catch ex As Exception  
                ' You might want to pass these errors  
                ' back out to the caller.  
                Console.WriteLine("Error: {0}", ex.Message)  
            End Try  
        End Using  
    End Sub  
  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
  
        ' If you have not included "Asynchronous Processing=true"
        ' in the connection string, the command will not be able  
        ' to execute asynchronously.  
        Return "Data Source=(local);Integrated Security=SSPI;" & _  
          "Initial Catalog=AdventureWorks; " & _  
          "Asynchronous Processing=true"  
    End Function  
End Module
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Class1  
{  
    [STAThread]  
    static void Main()  
    {  
        // The WAITFOR statement simply adds enough time to
        // prove the asynchronous nature of the command.  
  
        string commandText =  
          "UPDATE Production.Product SET ReorderPoint = " +  
          "ReorderPoint + 1 " +  
          "WHERE ReorderPoint Is Not Null;" +  
          "WAITFOR DELAY '0:0:3';" +  
          "UPDATE Production.Product SET ReorderPoint = " +  
          "ReorderPoint - 1 " +  
          "WHERE ReorderPoint Is Not Null";  
  
        RunCommandAsynchronously(  
            commandText, GetConnectionString());  
  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  
    private static void RunCommandAsynchronously(  
      string commandText, string connectionString)  
    {  
        // Given command text and connection string, asynchronously  
        // execute the specified command against the connection.
        // For this example, the code displays an indicator as it's
        // working, verifying the asynchronous behavior.
        using (SqlConnection connection =  
          new SqlConnection(connectionString))  
        {  
            try  
            {  
                int count = 0;  
                SqlCommand command =
                    new SqlCommand(commandText, connection);  
                connection.Open();  
  
                IAsyncResult result =
                    command.BeginExecuteNonQuery();  
                while (!result.IsCompleted)  
                {  
                    Console.WriteLine(  
                                    "Waiting ({0})", count++);  
                    // Wait for 1/10 second, so the counter  
                    // doesn't consume all available
                    // resources on the main thread.  
                    System.Threading.Thread.Sleep(100);  
                }  
                Console.WriteLine(  
                    "Command complete. Affected {0} rows.",  
                command.EndExecuteNonQuery(result));  
            }  
            catch (SqlException ex)  
            {  
                Console.WriteLine("Error ({0}): {1}",
                    ex.Number, ex.Message);  
            }  
            catch (InvalidOperationException ex)  
            {  
                Console.WriteLine("Error: {0}", ex.Message);  
            }  
            catch (Exception ex)  
            {  
                // You might want to pass these errors  
                // back out to the caller.  
                Console.WriteLine("Error: {0}", ex.Message);  
            }  
        }  
    }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,
        // you can retrieve it from a configuration file.
  
        // If you have not included "Asynchronous Processing=true"  
        // in the connection string, the command will not be able  
        // to execute asynchronously.  
        return "Data Source=(local);Integrated Security=SSPI;" +  
        "Initial Catalog=AdventureWorks; " +
        "Asynchronous Processing=true";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="10016-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="10016-111">See also</span></span>

- [<span data-ttu-id="10016-112">Asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="10016-112">Asynchronous Operations</span></span>](asynchronous-operations.md)
- [<span data-ttu-id="10016-113">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="10016-113">ADO.NET Overview</span></span>](../ado-net-overview.md)

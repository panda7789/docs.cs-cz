---
title: Jeden hromadné operace kopírování
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 37402672a6df808cb5e1c2424817fd9ce749cc82
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="single-bulk-copy-operations"></a>Jeden hromadné operace kopírování
Nejjednodušším přístupem při provádění operace hromadného kopírování systému SQL Server je provést najednou proti databázi. Ve výchozím nastavení, se provádí operace hromadného kopírování jako izolované operaci: způsobem, beztransakční, dojde k kopírování s distribucí nebude mít možnost zpět.  
  
> [!NOTE]
>  Pokud je nutné vrátit zpět nebo jeho část hromadné kopírování když dojde k chybě, můžete použít <xref:System.Data.SqlClient.SqlBulkCopy>-spravované transakce, nebo provádět hromadné kopírování v rámci existující transakce. **SqlBulkCopy** také pracovat se <xref:System.Transactions> Pokud toto připojení je uvedené (implicitně nebo explicitně) do **System.Transactions** transakce.  
>   
>  Další informace najdete v tématu [transakce a operace hromadného kopírování](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).  
  
 K provedení operace hromadného kopírování obecné kroky jsou následující:  
  
1.  Připojte zdrojový server a získejte data, která mají být zkopírovány. Data mohou pocházet také z jiných zdrojů, pokud se dá načíst z <xref:System.Data.IDataReader> nebo <xref:System.Data.DataTable> objektu.  
  
2.  Připojení k cílovému serveru (Pokud chcete, aby **SqlBulkCopy** k navázání připojení pro vás).  
  
3.  Vytvoření <xref:System.Data.SqlClient.SqlBulkCopy> objektu, nastavení všechny nezbytné vlastnosti.  
  
4.  Nastavte **DestinationTableName** vlastnost označující v cílové tabulce hromadného vložení operaci.  
  
5.  Volání jednoho z **WriteToServer** metody.  
  
6.  Volitelně můžete aktualizovat vlastnosti a volání **WriteToServer** opakujte podle potřeby.  
  
7.  Volání <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, nebo zabalení operace hromadného kopírování v rámci `Using` příkaz.  
  
> [!CAUTION]
>  Doporučujeme, aby odpovídaly zdrojové a cílové datové typy sloupce. Pokud tyto datové typy se neshodují, **SqlBulkCopy** pokusí převést hodnotu každý zdroj cílového typu dat, pomocí pravidel zaměstnaní <xref:System.Data.SqlClient.SqlParameter.Value%2A>. Převody může ovlivnit výkon a také může způsobit neočekávané chyby. Například `Double` možné převést na datový typ `Decimal` datový typ většinu času, ale ne vždy.  
  
## <a name="example"></a>Příklad  
 Následující aplikace konzoly ukazuje, jak načíst data pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy. V tomto příkladu <xref:System.Data.SqlClient.SqlDataReader> se používá ke zkopírování dat z **Production.Product** tabulky v systému SQL Server**AdventureWorks** databáze do podobné tabulky ve stejné databázi.  
  
> [!IMPORTANT]
>  Tato ukázka se nespustí, pokud jste vytvořili pracovní tabulky, jak je popsáno v [hromadné kopírování příklad instalace](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Tento kód je určen k předvedení syntaxe pro používání **SqlBulkCopy** pouze. Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je snadnější a rychlejší pomocí jazyka Transact-SQL `INSERT … SELECT` příkaz Kopírovat data.  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Provádění operace hromadného kopírování pomocí Transact-SQL a třídu příkazu  
 Následující příklad ukazuje, jak používat <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metoda příkaz BULK INSERT nelze provést.  
  
> [!NOTE]
>  Cesta k souboru pro zdroj dat je relativní k serveru. Proces serveru musí mít přístup k této cestě v pořadí pro hromadné kopírování proběhla úspěšně.  
  
```vb  
Using connection As SqlConnection = New SqlConnection(connectionString)  
Dim queryString As String = _  
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _  
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"  
connection.Open()  
SqlCommand command = New SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Operace hromadného kopírování na SQL Serveru](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

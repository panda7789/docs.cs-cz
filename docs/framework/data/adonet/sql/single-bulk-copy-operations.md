---
title: Jednorázové operace hromadného kopírování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 286199a595e7b34c25fcc13d37c5c913f269304d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555190"
---
# <a name="single-bulk-copy-operations"></a>Jednorázové operace hromadného kopírování
Nejjednodušším přístupem při provádění hromadného kopírování systému SQL Server je k provedení jedné operace proti databázi. Ve výchozím nastavení, se provádí operaci hromadného kopírování jako izolované operace: způsobem beztransakční, dojde k operaci kopírování s distribucí nebude mít možnost zpět.  
  
> [!NOTE]
>  Pokud je potřeba vrátit zpět nebo její část hromadného kopírování při výskytu chyby, můžete použít <xref:System.Data.SqlClient.SqlBulkCopy>– spravované transakce, nebo provést operaci hromadného kopírování v rámci existující transakce. **SqlBulkCopy** budou fungovat i pro <xref:System.Transactions> Pokud připojení zařazen (implicitně nebo explicitně) do **System.Transactions** transakce.  
>   
>  Další informace najdete v tématu [transakce a operace hromadného kopírování](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).  
  
 Obecné kroky pro provedení operace hromadného kopírování jsou následující:  
  
1.  Připojit ke zdrojovému serveru a získat data, která mají být zkopírovány. Data mohou pocházet také z jiných zdrojů, pokud se dá načíst ze <xref:System.Data.IDataReader> nebo <xref:System.Data.DataTable> objektu.  
  
2.  Připojení k cílovému serveru (Pokud chcete, aby **SqlBulkCopy** k navázání připojení pro vás).  
  
3.  Vytvoření <xref:System.Data.SqlClient.SqlBulkCopy> objekt nastavení všechny nezbytné vlastnosti.  
  
4.  Nastavte **DestinationTableName** vlastnost umožňující označit v cílové tabulce hromadného vložení operace.  
  
5.  Volání jednoho z **WriteToServer** metody.  
  
6.  Volitelně můžete aktualizovat vlastnosti a volání **WriteToServer** opakujte podle potřeby.  
  
7.  Volání <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, nebo zabalovat operace hromadného kopírování v rámci `Using` příkazu.  
  
> [!CAUTION]
>  Doporučujeme vám, že datové typy sloupce zdrojovou a cílovou odpovídají. Pokud datové typy, které se neshodují, **SqlBulkCopy** pokusí převést hodnotu každého zdroje do cílového typu dat, pomocí pravidel náhradník <xref:System.Data.SqlClient.SqlParameter.Value%2A>. Převody může ovlivnit výkon a může také způsobit neočekávané chyby. Například `Double` datového typu lze převést na `Decimal` datový typ většinu času, ale ne vždy.  
  
## <a name="example"></a>Příklad  
 Následující konzolové aplikace ukazuje, jak načíst data pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy. V tomto příkladu <xref:System.Data.SqlClient.SqlDataReader> se použije ke zkopírování dat z **Production.Product** tabulka na SQL serveru **AdventureWorks** databáze do podobné tabulky ve stejné databázi.  
  
> [!IMPORTANT]
>  Tato ukázka se nespustí, pokud jste vytvořili pracovní tabulky, jak je popsáno v [příklad nastavení hromadného kopírování](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Tento kód je k dispozici k předvedení syntaxe pro používání **SqlBulkCopy** pouze. Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je jednodušší a rychlejší použití příkazů jazyka Transact-SQL `INSERT … SELECT` příkaz Kopírovat data.  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Provedení operace hromadného kopírování pomocí jazyka Transact-SQL a třídu příkazu  
 Následující příklad ukazuje způsob použití <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody k provedení příkazu BULK INSERT.  
  
> [!NOTE]
>  Cesta k souboru pro zdroj dat je relativní k serveru. Proces serveru musí mít přístup k této cestě v pořadí pro operaci hromadného kopírování úspěšné.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Operace hromadného kopírování na SQL Serveru](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

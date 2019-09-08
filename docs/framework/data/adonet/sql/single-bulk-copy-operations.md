---
title: Jednorázové operace hromadného kopírování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 05e3cf25352e731d320061001f08a835cd520b15
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780926"
---
# <a name="single-bulk-copy-operations"></a>Jednorázové operace hromadného kopírování

Nejjednodušší způsob, jak provádět operace hromadného kopírování SQL Server, je provést jednu operaci s databází. Ve výchozím nastavení se operace hromadného kopírování provádí jako izolovaná operace: operace kopírování probíhá v netransakčním režimu bez příležitostí pro vrácení zpět.

> [!NOTE]
> Pokud potřebujete vrátit zpátky veškerou nebo část hromadného kopírování, když dojde k chybě, můžete buď použít <xref:System.Data.SqlClient.SqlBulkCopy>transakci spravovanou, nebo provést operaci hromadného kopírování v rámci existující transakce. **SqlBulkCopy** bude také fungovat s <xref:System.Transactions> , pokud je připojení zařazeno (implicitně nebo explicitně) do transakce **System. Transactions** .
>
> Další informace najdete v tématu [transakce a operace hromadného kopírování](transaction-and-bulk-copy-operations.md).

Pro provedení hromadné operace kopírování jsou k dishlavní kroky následující:

1. Připojte se ke zdrojovému serveru a Získejte data, která se mají zkopírovat. Data mohou být také převzata z jiných zdrojů, pokud je lze načíst z <xref:System.Data.IDataReader> objektu <xref:System.Data.DataTable> nebo.

2. Připojte se k cílovému serveru (Pokud nechcete, aby **SqlBulkCopy** navázalo připojení).

3. <xref:System.Data.SqlClient.SqlBulkCopy> Vytvořte objekt a nastavte potřebné vlastnosti.

4. Nastavte vlastnost **DestinationTableName** tak, aby označovala cílovou tabulku pro operaci hromadného vložení.

5. Zavolejte jednu z metod **WriteToServer** .

6. Volitelně můžete aktualizovat vlastnosti a znovu volat **WriteToServer** podle potřeby.

7. Volání <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>nebo zabalení operací hromadného kopírování `Using` v rámci příkazu.

> [!CAUTION]
> Doporučujeme, aby se shodovaly datové typy zdrojového a cílového sloupce. Pokud se datové typy neshodují, **SqlBulkCopy** se pokusí převést jednotlivé zdrojové hodnoty na cílový datový typ pomocí pravidel používaných v <xref:System.Data.SqlClient.SqlParameter.Value%2A>. Převod může ovlivnit výkon a může také vést k neočekávaným chybám. Například `Double` datový typ lze převést `Decimal` na datový typ většinou v čase, ale ne vždy.

## <a name="example"></a>Příklad

Následující aplikace konzoly ukazuje, jak načíst data pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy. V tomto příkladu <xref:System.Data.SqlClient.SqlDataReader> se používá ke kopírování dat z tabulky **produkčního produktu** v databázi SQL Server **AdventureWorks** do podobné tabulky ve stejné databázi.

> [!IMPORTANT]
> Tato ukázka nebude spuštěna, pokud jste nevytvořili pracovní tabulky, jak je popsáno v tématu [hromadné kopírování – příklad nastavení](bulk-copy-example-setup.md). Tento kód je k dispozici k předvedení syntaxe pouze pro použití **SqlBulkCopy** . Pokud se zdrojové a cílové tabulky nacházejí ve stejné instanci SQL Server, je snazší a rychlejší použít příkaz Transact-SQL `INSERT … SELECT` ke zkopírování dat.

[!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
[!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]

## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Provádění operace hromadného kopírování s použitím jazyka Transact-SQL a třídy příkazu

Následující příklad ukazuje, jak použít <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metodu ke spuštění příkazu Bulk INSERT.

> [!NOTE]
> Cesta k souboru pro zdroj dat je relativní vzhledem k serveru. Aby operace hromadného kopírování proběhla úspěšně, musí mít proces serveru přístup k této cestě.

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

- [Operace hromadného kopírování na SQL Serveru](bulk-copy-operations-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)

---
title: Vytváření výčtu instancí SQL Serveru (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: 304387197c7c6ca31d76ce429cd1516be27ba7b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938178"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Vytváření výčtu instancí SQL Serveru (ADO.NET)
SQL Server umožňuje aplikacím najít SQL Server instance v rámci aktuální sítě. Třída zpřístupňuje tyto informace vývojáři aplikace a <xref:System.Data.DataTable> poskytuje informace o všech viditelných serverech. <xref:System.Data.Sql.SqlDataSourceEnumerator> Tato vrácená tabulka obsahuje seznam instancí serveru dostupných v síti, které se shodují se seznamem zadaným při pokusu uživatele o vytvoření nového připojení, a rozbalí rozevírací seznam obsahující všechny dostupné servery ve **vlastnostech připojení.** dialogové okno. Zobrazené výsledky nejsou vždy dokončeny.  
  
> [!NOTE]
> Stejně jako u většiny služeb Windows je nejlepší spustit službu SQL Browser s nejmenšími možnými oprávněními. Další informace o službě SQL Browser a o tom, jak spravovat její chování, najdete v tématu SQL Server Books Online.  
  
## <a name="retrieving-an-enumerator-instance"></a>Načítání instance enumerátoru  
 Aby bylo možné načíst tabulku obsahující informace o dostupných instancích SQL Server, je nutné nejprve načíst enumerátor pomocí vlastnosti Shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> :  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Po načtení statické instance můžete zavolat <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metodu, která <xref:System.Data.DataTable> vrátí obsahující informace o dostupných serverech:  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 Tabulka vrácená voláním metody obsahuje následující sloupce, z nichž všechny obsahují `string` hodnoty:  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**ServerName**|Název serveru.|  
|**InstanceName**|Název instance serveru. Prázdné, pokud server běží jako výchozí instance.|  
|**Clusterované**|Označuje, zda je Server součástí clusteru.|  
|**Verze**|Verze serveru. Příklad:<br /><br /> -9.00. x (SQL Server 2005)<br />-   10.0.xx (SQL Server 2008)<br />-   10.50.x (SQL Server 2008 R2)<br />-   11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Omezení výčtu  
 Všechny dostupné servery můžou nebo nemusí být uvedené. Seznam se může lišit v závislosti na faktorech, jako jsou například časové limity a síťový provoz. To může způsobit, že se seznam bude lišit od dvou po sobě jdoucích volání. Zobrazí se pouze servery ve stejné síti. Pakety všesměrového vysílání obvykle nebudou procházet směrovači, což znamená, že se server nemusí zobrazovat, ale bude stabilní v rámci volání.  
  
 Uvedené servery můžou nebo nemusí mít další informace, jako je `IsClustered` verze a. To závisí na tom, jak byl seznam získán. Servery uvedené prostřednictvím služby SQL Server Browser budou mít více podrobností, než jaké jsou nalezeny prostřednictvím infrastruktury systému Windows, ve které bude uveden pouze název.  
  
> [!NOTE]
> Výčet serveru je k dispozici pouze při spuštění v úplném vztahu důvěryhodnosti. Sestavení spuštěná v částečně důvěryhodném prostředí ji nebudou moct používat, i když mají <xref:System.Data.SqlClient.SqlClientPermission> oprávnění zabezpečení přístupu kódu (CAS).  
  
 SQL Server poskytuje informace pro <xref:System.Data.Sql.SqlDataSourceEnumerator> použití externí služby systému Windows s názvem SQL Browser. Tato služba je ve výchozím nastavení povolená, ale správci ji můžou vypnout nebo zakázat, takže instance serveru není pro tuto třídu viditelná.  
  
## <a name="example"></a>Příklad  
 Následující aplikace konzoly načte informace o všech viditelných instancích SQL Server a zobrazí informace v okně konzoly.  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

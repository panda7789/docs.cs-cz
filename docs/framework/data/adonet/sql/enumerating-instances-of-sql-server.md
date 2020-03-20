---
title: Výčet instancí serveru SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: a707df533216613e34d9f357c7b9e035f73b9561
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148683"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Vytváření výčtu instancí SQL Serveru (ADO.NET)
SQL Server umožňuje aplikacím najít instance serveru SQL Server v rámci aktuální sítě. Třída <xref:System.Data.Sql.SqlDataSourceEnumerator> zpřístupňuje tyto informace vývojáři <xref:System.Data.DataTable> aplikace a poskytuje informace o všech viditelných serverech. Tato vrácená tabulka obsahuje seznam instancí serveru dostupných v síti, který odpovídá seznamu poskytnutému při pokusu uživatele o vytvoření nového připojení, a rozbalí rozevírací seznam obsahující všechny dostupné servery v dialogovém okně **Vlastnosti připojení.** Zobrazené výsledky nejsou vždy úplné.  
  
> [!NOTE]
> Stejně jako u většiny služeb systému Windows je nejlepší spustit službu prohlížeče SQL s co nejmenšími oprávněními. Další informace o službě prohlížeče SQL Browser a způsob správy jejího chování naleznete v tématu SQL Server Books Online.  
  
## <a name="retrieving-an-enumerator-instance"></a>Načítání instance čítače výčtu  
 Chcete-li načíst tabulku obsahující informace o dostupných instancích serveru SQL Server, musíte nejprve načíst čítače enumerator pomocí sdílené/statické <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> vlastnosti:  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Po načtení statické instance můžete volat <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metodu, která <xref:System.Data.DataTable> vrací obsahující informace o dostupných serverech:  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 Tabulka vrácená z volání metody obsahuje následující sloupce, které obsahují `string` hodnoty:  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název_serveru**|Název serveru.|  
|**Název_instance**|Název instance serveru. Pokud je server spuštěn jako výchozí instance, je prázdné.|  
|**Jeseskupený**|Označuje, zda je server součástí clusteru.|  
|**Verze**|Verze serveru. Například:<br /><br /> - 9.00.x (SQL Server 2005)<br />- 10.0.xx (SQL Server 2008)<br />- 10.50.x (SQL Server 2008 R2)<br />- 11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Omezení výčtu  
 Všechny dostupné servery mohou nebo nemusí být uvedeny. Seznam se může lišit v závislosti na faktorech, jako jsou časové osy a síťový provoz. To může způsobit, že seznam se liší na dvě po sobě jdoucí volání. Budou uvedeny pouze servery ve stejné síti. Všesměrové pakety obvykle nebudou procházet směrovači, což je důvod, proč se nemusí zobrazit uvedený server, ale bude stabilní napříč voláními.  
  
 Uvedené servery mohou nebo nemusí `IsClustered` mít další informace, jako je například a verze. To závisí na způsobu získání seznamu. Servery uvedené prostřednictvím služby prohlížeče SQL Server budou mít více podrobností než servery nalezené prostřednictvím infrastruktury systému Windows, která bude uvádět pouze název.  
  
> [!NOTE]
> Výčet serveru je k dispozici pouze při spuštění v plné důvěryhodnosti. Sestavení spuštěná v částečně důvěryhodném prostředí jej nebudou moci používat, <xref:System.Data.SqlClient.SqlClientPermission> a to ani v případě, že mají oprávnění CAS (Code Access Security).  
  
 SQL Server poskytuje <xref:System.Data.Sql.SqlDataSourceEnumerator> informace pro použití externí služby Windows s názvem SQL Browser. Tato služba je ve výchozím nastavení povolena, ale správci ji mohou vypnout nebo zakázat, čímž se instance serveru pro tuto třídu stane neviditelnou.  
  
## <a name="example"></a>Příklad  
 Následující konzolová aplikace načte informace o všech viditelných instancích serveru SQL Server a zobrazí informace v okně konzoly.  
  
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
  
## <a name="see-also"></a>Viz také

- [SQL Server a ADO.NET](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)

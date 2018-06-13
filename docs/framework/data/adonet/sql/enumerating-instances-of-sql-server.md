---
title: Vytváření výčtu instancí systému SQL Server (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: d9456926b228fadca940f6c4698829494382e237
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355519"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Vytváření výčtu instancí systému SQL Server (ADO.NET)
SQL Server povoluje aplikace najít instance systému SQL Server v rámci aktuální sítě. <xref:System.Data.Sql.SqlDataSourceEnumerator> Třída zpřístupňuje tyto informace pro vývojáře aplikací, zajištění <xref:System.Data.DataTable> obsahující informace o všech viditelné serverech. To vrácena tabulka obsahuje seznam instancí serverů, které jsou k dispozici v síti, která odpovídá seznamu zadat, když se uživatel pokusí o vytvoření nového připojení a rozbalí rozevírací seznam obsahující všechny dostupné servery na **připojení Vlastnosti** dialogové okno. Výsledky zobrazí vždy nebyly dokončeny.  
  
> [!NOTE]
>  Jako s většina služeb systému Windows, je vhodné spustit službu SQL Browser s nejmenšími možnými oprávněními. Další informace o služba SQL Browser a jak spravovat své chování najdete v části SQL Server Books Online.  
  
## <a name="retrieving-an-enumerator-instance"></a>Načítání Instance enumerátor  
 Chcete-li načíst tabulku obsahující informace o dostupných instancí systému SQL Server, musíte nejdřív načíst enumerátor pomocí sdílených/statické <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> vlastnost:  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Po načtení statická instance, můžete zavolat <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metoda, která vrátí hodnotu <xref:System.Data.DataTable> obsahující informace o dostupných serverů:  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 Tabulka vrácená z volání metody, které obsahuje následující sloupce, které obsahují `string` hodnoty:  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**ServerName**|Název serveru.|  
|**InstanceName**|Název instance serveru. Prázdná, pokud je server spuštěn jako výchozí instanci.|  
|**IsClustered**|Určuje, zda je server součástí clusteru.|  
|**Verze**|Verze serveru. Příklad:<br /><br /> -9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])<br />-10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])<br />-10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])<br />-11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Omezení – výčet  
 Všechny dostupné servery může nebo nemusí být uvedena. Seznam se může lišit v závislosti na faktorech, jako je například časové limity a síťový provoz. To může způsobit seznamu jiné na dvě po sobě jdoucí volání. Objeví se pouze servery ve stejné síti. Paketů všesměrového vysílání obvykle nebude přes směrovače, proto nemusíte vidět server uvedený, ale bude stabilní napříč volání.  
  
 Uvedené servery může nebo nemusí mít další informace, jako `IsClustered` a verze. Toto je závisí na způsobu získání seznamu. Další podrobnosti, než jsou prostřednictvím infrastrukturu nástroje systému Windows, která se zobrazí seznam pouze název bude mít servery uvedené přes službu SQL Server browser.  
  
> [!NOTE]
>  Výčet serveru je k dispozici pouze při spuštění v plné důvěryhodnosti. Sestavení v prostředí částečně důvěryhodné nebude možné použít, i když <xref:System.Data.SqlClient.SqlClientPermission> oprávnění zabezpečení přístupu kódu (CAS).  
  
 Poskytuje informace o systému SQL Server <xref:System.Data.Sql.SqlDataSourceEnumerator> prostřednictvím externí službu systému Windows s názvem SQL Browser. Tato služba je ve výchozím nastavení povoleno, ale správci vypnout nebo ji zakázat, viditelnosti instance serveru pro tuto třídu.  
  
## <a name="example"></a>Příklad  
 Následující konzolové aplikace načte informace o všech viditelné instance systému SQL Server a zobrazí informace v okně konzoly.  
  
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
 [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

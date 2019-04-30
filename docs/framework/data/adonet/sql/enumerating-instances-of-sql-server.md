---
title: Vytváření výčtu instancí SQL Serveru (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: a723679fe18352e115df78af72975097dc28b617
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877588"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Vytváření výčtu instancí SQL Serveru (ADO.NET)
SQL Server povoluje aplikací, aby našel instance systému SQL Server v rámci aktuální sítě. <xref:System.Data.Sql.SqlDataSourceEnumerator> Třída zpřístupňuje tyto informace pro vývojáře aplikací, poskytování <xref:System.Data.DataTable> obsahující informace o všech serverech viditelné. To vrácena tabulka obsahuje seznam instancí serveru, dostupný v síti, která odpovídá seznamu, pokud uživatel se pokusí vytvořit nové připojení a rozbalí rozevírací seznam obsahující všechny dostupné servery na **připojení Vlastnosti** dialogové okno. Výsledky zobrazené nejsou vždy úplný.  
  
> [!NOTE]
>  Stejně jako u většiny služby Windows to je vhodné spustit službu SQL Browser s nejmenšími možnými oprávněními. Další informace o službu SQL Browser a jak spravovat své chování naleznete v tématu knihy Online SQL Server.  
  
## <a name="retrieving-an-enumerator-instance"></a>Načítání Instance výčtu  
 Aby bylo možné načíst tabulku obsahující informace o dostupných instancí systému SQL Server, musíte nejdřív načíst enumerátor pomocí sdílených/statické <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> vlastnost:  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Po načtení statická instance volejte <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metoda, která vrátí <xref:System.Data.DataTable> obsahující informace o dostupných serverů:  
  
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
|**InstanceName**|Název instance serveru. Prázdné, pokud je server spuštěn jako výchozí instanci.|  
|**IsClustered**|Určuje, zda je server součástí clusteru.|  
|**Verze**|Verze serveru. Příklad:<br /><br /> -9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])<br />-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])<br />-10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])<br />-   11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Výčet omezení  
 Všechny dostupné servery může nebo nemusí být uvedená. Seznam se může lišit v závislosti na faktorech, třeba vypršení časových limitů a síťové přenosy. To může způsobit seznamem, aby se na dvě po sobě jdoucích volání lišit. Zobrazí se pouze servery ve stejné síti. Pakety všesměrového vysílání obvykle nebudete procházet směrovače, proto nemusíte vidět serveru uvedené, ale bude stabilní napříč volání.  
  
 Uvedené servery může nebo nemusí mít další informace, jako `IsClustered` a verze. To závisí na způsobu získání seznamu. Servery uvedené přes službu systému SQL Server browser budou mít informace než přes infrastrukturu Windows, který zobrazí seznam pouze název.  
  
> [!NOTE]
>  Výčet server je dostupná jenom při spouštění v režimu úplné důvěryhodnosti. Spuštění v prostředí částečně důvěryhodných sestavení nebudou moct používat, i v případě, že mají <xref:System.Data.SqlClient.SqlClientPermission> oprávnění zabezpečení přístupu kódu (CAS).  
  
 Obsahuje informace o systému SQL Server <xref:System.Data.Sql.SqlDataSourceEnumerator> prostřednictvím externí služby Windows s názvem SQL Browser. Tato služba je ve výchozím nastavení povoleno, ale správci vypnout nebo zakázat, neviditelný instance serveru k této třídě.  
  
## <a name="example"></a>Příklad  
 Následující konzolové aplikace načte informace o všech viditelných instancí systému SQL Server a zobrazí informace v okně konzoly.  
  
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
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

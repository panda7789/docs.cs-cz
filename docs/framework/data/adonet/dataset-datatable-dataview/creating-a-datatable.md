---
title: Vytváření DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: a374c7c6e7dfc04cd8828208d6762f8d8665072e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-datatable"></a>Vytváření DataTable
A <xref:System.Data.DataTable>, která představuje jednu tabulku v paměti relačních dat, lze vytvořit a používat samostatně nebo je můžete použít jiné objekty rozhraní .NET Framework nejčastěji jako člen skupiny <xref:System.Data.DataSet>.  
  
 Můžete vytvořit **DataTable** objekt pomocí odpovídající **DataTable** konstruktor. Můžete přidat jej do **datovou sadu** pomocí **přidat** metodu ho přidat do **DataTable** objektu **tabulky** kolekce.  
  
 Můžete také vytvořit **DataTable** objekty v rámci **datovou sadu** pomocí **vyplnění** nebo **FillSchema** metody  **DataAdapter** objekt, nebo z předdefinovaných nebo vyvozen XML schématu pomocí **ReadXml**, **ReadXmlSchema**, nebo **InferXmlSchema** metody **datovou sadu**. Všimněte si, že po přidání **DataTable** jako člena **tabulky** kolekce jednoho **datovou sadu**, nelze ji přidat do kolekce tabulek jiných **Datovou sadu**.  
  
 Při prvním vytvoření **DataTable**, nemá schéma (to znamená, struktura). K definování schématu tabulky, musíte vytvořit a přidat <xref:System.Data.DataColumn> objekty ke **sloupce** kolekce tabulky. Můžete také definovat sloupec primárního klíče tabulky a vytvořit a přidat **omezení** objekty ke **omezení** kolekce tabulky. Po definování schématu pro **DataTable**, můžete přidat řádky dat do tabulky přidáním **DataRow** objekty ke **řádky** kolekce tabulky.  
  
 Není nutné zadat hodnotu <xref:System.Data.DataTable.TableName%2A> vlastnost při vytváření **DataTable**; můžete zadat vlastnost v jinou dobu, nebo můžete nechat prázdné. Pokud však přidáte tabulku bez **TableName** hodnotu **datovou sadu**, v tabulce bude mít přírůstkové výchozí název tabulky*N*, od verze "Tabulka" pro Table0.  
  
> [!NOTE]
>  Doporučujeme, abyste "tabulky*N*" zásady vytváření názvů, když zadáte **TableName** hodnota, protože název je zadat může dojít ke konfliktu s existujícím názvem výchozí tabulky v **datové sady** . Pokud se zadaným názvem již existuje, je vyvolána výjimka.  
  
 Následující příklad vytvoří instanci **DataTable** objektu a přiřadí ji název "Zákazníci".  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 Následující příklad vytvoří instanci **DataTable** přidáním jeho **tabulky** kolekce **datovou sadu**.  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Naplnění datové sady z adaptéru dat](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

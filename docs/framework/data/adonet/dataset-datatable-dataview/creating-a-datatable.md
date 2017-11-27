---
title: "Vytváření DataTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 923d19e9539c6d93f3714efcdaa6fe7a5da843ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Naplnění datové sady z modul DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Načítání datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Načítání informací o schématu sady dat z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

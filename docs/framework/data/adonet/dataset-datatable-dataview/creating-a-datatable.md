---
title: Vytvoření datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: ad3f8bc6b42c5a54b42100a5d010e097ba80adc2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386910"
---
# <a name="creating-a-datatable"></a>Vytvoření datové tabulky
A <xref:System.Data.DataTable>, která představuje jednu tabulku relační data v paměti, lze vytvořit a používat samostatně nebo mohou využívat jiné objekty rozhraní .NET Framework nejčastěji jako člen <xref:System.Data.DataSet>.  
  
 Můžete vytvořit **DataTable** s použitím příslušná **DataTable** konstruktoru. Můžete přidat tak **datovou sadu** pomocí **přidat** metoda a přidejte ji tak **DataTable** objektu **tabulky** kolekce.  
  
 Můžete také vytvořit **DataTable** objekty v rámci **datovou sadu** pomocí **vyplnit** nebo **FillSchema** metody  **Vlastnost DataAdapter** objektu, nebo z předdefinovaných nebo odvozené XML schématu pomocí **ReadXml**, **ReadXmlSchema**, nebo **InferXmlSchema** metody **datovou sadu**. Všimněte si, že po přidání **DataTable** jako člen **tabulky** kolekce jednoho **datovou sadu**, ho nemůžete přidat do kolekce tabulek jiných **Datovou sadu**.  
  
 Při prvním vytvoření **DataTable**, nemá schématu (to znamená, že struktura). Definovat schéma tabulky, můžete vytvořit a přidat <xref:System.Data.DataColumn> objektů **sloupce** kolekce v tabulce. Můžete také definujte sloupec primárního klíče pro tabulku a vytvoříte a přidáte **omezení** objektů **omezení** kolekce v tabulce. Po definování schématu **DataTable**, řádky dat do tabulky můžete přidat tak, že přidáte **DataRow** objektů **řádky** kolekce tabulky.  
  
 Není nutné zadat hodnotu <xref:System.Data.DataTable.TableName%2A> vlastnost při vytváření **DataTable**; můžete zadat vlastnost později, nebo můžete nechat prázdné. Ale při přidání tabulky bez **TableName** hodnota, která se **datovou sadu**, tabulce dostanou přírůstkové výchozí název tabulky*N*počínaje "Table" pro Table0.  
  
> [!NOTE]
>  Doporučujeme, abyste "tabulky*N*" zásady vytváření názvů, když zadáte **TableName** hodnotu, protože název zadáte dojít ke konfliktu s existujícím názvem výchozí tabulky v **datové sady** . Pokud zadaný název již existuje, je vyvolána výjimka.  
  
 Následující příklad vytvoří instanci **DataTable** objektu a přiřazuje mu název "Zákazníků."  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 Následující příklad vytvoří instanci **DataTable** tak, že ji přidáte **tabulky** kolekce **datovou sadu**.  
  
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
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

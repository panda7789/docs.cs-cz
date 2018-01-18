---
title: "Přidání existující omezení datové sady"
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
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2f2f6c60197b1d71feb13ca351ad19298e09ea56
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="adding-existing-constraints-to-a-dataset"></a>Přidání existující omezení datové sady
**Vyplnění** metodu **DataAdapter** doplní <xref:System.Data.DataSet> pouze se sloupci a řádky ze zdroje dat; tabulky ale omezení jsou běžně nastavit zdroj dat **vyplnění** metoda nepřidá tyto informace schématu **datovou sadu** ve výchozím nastavení. K naplnění **datovou sadu** s stávající informace o omezení primárního klíče ze zdroje dat, můžete buď volání **FillSchema** metodu **DataAdapter**, nebo nastavte **MissingSchemaAction** vlastnost **DataAdapter** k **AddWithKey** před voláním **vyplnění**. Tím bude zajištěno, že primární klíč omezení **datovou sadu** odrážejí hodnoty ve zdroji dat. Informace o omezení cizího klíče nezahrnuje a musí být vytvořen explicitně, jak je znázorněno v [DataTable omezení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Informace o schématu pro přidání **datovou sadu** před naplňování daty zajišťuje, aby byly součástí omezení primárního klíče <xref:System.Data.DataTable> objekty v **datovou sadu**. V důsledku toho, pokud další volání k vyplnění **datovou sadu** probíhají primární klíčový sloupec informace slouží tak, aby odpovídala nové záznamy ze zdroje dat s aktuální řádky v každé **DataTable**a aktuální data v v tabulkách se přepíše daty ze zdroje dat. Bez informace o schématu nové záznamy ze zdroje dat se připojí k **datovou sadu**, což je duplicitní řádky.  
  
> [!NOTE]
>  Pokud se identifikuje sloupce ve zdroji dat jako automatické zvyšování **FillSchema** metody nebo **vyplnění** metoda s **MissingSchemaAction** z  **AddWithKey**, vytvoří **DataColumn** s **AutoIncrement** vlastnost nastavena na hodnotu `true`. Nicméně, budete muset nastavit **AutoIncrementStep** a **AutoIncrementSeed** hodnoty sami. Další informace o automatické zvyšování sloupce najdete v tématu [vytváření sloupců AutoIncrement](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
 Pomocí **FillSchema** nebo nastavení **MissingSchemaAction** k **AddWithKey** vyžaduje další zpracování ve zdroji dat, které podávají informace sloupec primárního klíče. Další zpracování může bránit ve výkonu. Pokud znáte primární informace o klíči v době návrhu, doporučujeme vám, že explicitně zadáte sloupec primárního klíče nebo sloupce pro dosažení optimálního výkonu. Informace o explicitně nastavení primární informace o klíči pro tabulku najdete v tématu [definování primárních klíčů](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Následující příklad kódu ukazuje, jak přidat informace o schématu pro **datovou sadu** pomocí **FillSchema**.  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 Následující příklad kódu ukazuje, jak přidat informace o schématu pro **datovou sadu** pomocí **MissingSchemaAction.AddWithKey** vlastnost **vyplnění** metoda.  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a>Zpracování více sad výsledků dotazu  
 Pokud **DataAdapter** zaznamená více sad výsledků dotazu vrácená z **SelectCommand**, vytvoří několik tabulek v **datovou sadu**. V tabulkách přidělí nule přírůstkové výchozí název **tabulky** *N*, od verze **tabulky** místo "Table0". Pokud je název tabulky předat jako argument k **FillSchema** metody tabulky přidělí nule přírůstkové název **TableName** *N*, od verze **TableName** místo "TableName0".  
  
> [!NOTE]
>  Pokud **FillSchema** metodu **třídy OleDbDataAdapter** objektu se říká pro příkaz, který vrátí více sad výsledků dotazu, je vrácena pouze informace o schématu z první sadu výsledků dotazu. Při vrácení informací o schématu pro více výsledek nastaví pomocí **třídy OleDbDataAdapter**, doporučuje se, zda jste zadali **MissingSchemaAction** z **AddWithKey** a získat informace o schématu při volání metody **vyplnění** metoda.  
  
## <a name="see-also"></a>Viz také  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

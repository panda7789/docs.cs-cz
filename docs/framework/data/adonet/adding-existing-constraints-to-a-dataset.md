---
title: Přidání existujících omezení do datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 90aa1e5dceb3cac87d330837496b9dc467dc1876
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555469"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>Přidání existujících omezení do datové sady
**Vyplnit** metodu **DataAdapter** vyplní <xref:System.Data.DataSet> jenom pomocí sloupce tabulky a řádky ze zdroje dat, i když omezení běžně nastavené ve zdroji dat **vyplnit** metoda nepřidá informace o tomto schématu **datovou sadu** ve výchozím nastavení. K naplnění **datovou sadu** s stávající informace o omezení primárního klíče ze zdroje dat, můžete buď zavolat **FillSchema** metodu **DataAdapter**, nebo nastavte **MissingSchemaAction** vlastnost **DataAdapter** k **AddWithKey** před voláním **vyplnit**. To zajistí, že primární klíče omezení **datovou sadu** odrážejí hodnoty ve zdroji dat. Informace o omezení pro cizí klíč nezahrnuje a musí být vytvořen explicitně, jak je znázorněno v [omezení datových tabulek](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Přidání informací o schématu pro **datovou sadu** před naplňování daty zajistí, že jsou součástí omezení primárního klíče <xref:System.Data.DataTable> objekty v **datovou sadu**. V důsledku toho při dalších volání tak, aby vyplnil **datovou sadu** probíhají primární informace o sloupci klíče se používá tak, aby odpovídala nové řádky ze zdroje dat s aktuální řádky v každém **DataTable**a aktuální data s daty ze zdroje dat je přepsán v tabulkách. Bez informace o schématu, nových řádků ze zdroje dat jsou připojeny k **datovou sadu**výsledkem duplicitní řádky.  
  
> [!NOTE]
>  Pokud sloupce ve zdroji dat se identifikuje jako automatické zvyšování **FillSchema** metodu, nebo **vyplnit** metodou **MissingSchemaAction** z  **AddWithKey**, vytvoří **DataColumn** s **AutoIncrement** nastavenou na `true`. Ale budete muset nastavit **AutoIncrementStep** a **AutoIncrementSeed** hodnoty sami. Další informace o automatické zvyšování sloupců, naleznete v tématu [vytváření sloupců s automatickým navyšováním](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
 Pomocí **FillSchema** nebo nastavení **MissingSchemaAction** k **AddWithKey** vyžaduje další zpracování na zdroj dat zjistit informace o sloupec primárního klíče. Tato další zpracování může bránit výkonu. Pokud víte, informace o primárním klíči v době návrhu, doporučujeme, že explicitně neurčíte sloupec primárního klíče nebo sloupce, abyste dosáhli optimálního výkonu. Informace o explicitním nastavením informacemi o primárním klíči pro tabulku, naleznete v tématu [definování primárních klíčů](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Následující příklad kódu ukazuje, jak přidat informace o schématu **datovou sadu** pomocí **FillSchema**.  
  
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
  
 Následující příklad kódu ukazuje, jak přidat informace o schématu **datovou sadu** pomocí **MissingSchemaAction.AddWithKey** vlastnost **vyplnit** metoda.  
  
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
 Pokud **DataAdapter** nalezne více sad výsledků dotazu vrácená **SelectCommand**, vytvoří více tabulek v **datovou sadu**. Tabulky dostanou od nuly přírůstkové výchozí název **tabulky** *N*počínaje **tabulky** namísto "Table0". Pokud zadáte název tabulky je předán jako argument **FillSchema** metody tabulky dostanou od nuly přírůstkové název **TableName** *N*počínaje **TableName** namísto "TableName0".  
  
> [!NOTE]
>  Pokud **FillSchema** metodu **objektu OleDbDataAdapter** objektu je volána pro příkaz, který vrátí více sad výsledků dotazu, se vrátí jenom informace o schématu z první sady výsledků. Při vrácení informací o schématu pro více výsledku nastaví pomocí **objektu OleDbDataAdapter**, doporučuje se, že zadáte **MissingSchemaAction** z **AddWithKey** a získat informace o schématu při volání **vyplnit** metody.  
  
## <a name="see-also"></a>Viz také  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

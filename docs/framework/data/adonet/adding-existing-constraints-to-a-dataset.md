---
title: Přidání existujících omezení do datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: db072692eba4044e854f25ff2c7f8c9960714018
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785108"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>Přidání existujících omezení do datové sady
Metoda **Fill** v metodě **DataAdapter** vyplní <xref:System.Data.DataSet> pouze sloupce tabulky a řádky ze zdroje dat; i když jsou omezení obvykle nastavena zdrojem dat, metoda **Fill** nepřidá tyto informace o schématu do  **Datová sada** ve výchozím nastavení. Chcete-li naplnit **datovou sadu** stávajícími informacemi o omezení primárního klíče ze zdroje dat, můžete buď zavolat metodu **FillSchema** objektu **DataAdapter**, nebo nastavit vlastnost **MissingSchemaAction** objektu **DataAdapter** do **AddWithKey** před voláním metody **Fill**. Tím se zajistí, aby omezení primárního klíče v **datové sadě** odrážela ta, která jsou ve zdroji dat. Informace o omezeních cizích klíčů nejsou zahrnuty a je nutné je vytvořit explicitně, jak je znázorněno v [omezeních DataTable](./dataset-datatable-dataview/datatable-constraints.md).  
  
 Přidání informací o schématu do **datové sady** předtím, než je naplní data, zajistí, že omezení primárního <xref:System.Data.DataTable> klíče jsou zahrnuta s objekty v **datové sadě**. Výsledkem je, že když se vytvoří další volání pro vyplnění **datové sady** , použijí se informace o sloupci primárního klíče, aby se shodovaly s novými řádky ze zdroje dat s aktuálními řádky v každém **objektu DataTable**a aktuální data v tabulkách byly přepsána daty z zdroj dat Bez informací o schématu se nové řádky ze zdroje dat připojí k **datové sadě**, což vede k duplicitním řádkům.  
  
> [!NOTE]
> Pokud je sloupec ve zdroji dat identifikován jako Automatický přírůstek, metoda **FillSchema** nebo metoda **Fill** s **MissingSchemaAction** **AddWithKey**, vytvoří **DataColumn** s vlastností **AutoIncrement** . Nastavte na `true`. Hodnoty **hodnota AutoIncrementStep** a **AutoIncrementSeed** ale budete muset nastavit sami. Další informace o automatických přírůstcích sloupců najdete v tématu [vytváření sloupců AutoIncrement](./dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
 Použití **FillSchema** nebo nastavení **MissingSchemaAction** na **AddWithKey** vyžaduje dodatečné zpracování ve zdroji dat za účelem určení informací o sloupci primárního klíče. Toto dodatečné zpracování může bránit výkonu. Pokud znáte informace o primárním klíči v době návrhu, doporučujeme explicitně zadat sloupec nebo sloupce primárního klíče, abyste dosáhli optimálního výkonu. Informace o explicitním nastavení informací o primárním klíči pro tabulku najdete v tématu [Definování primárních klíčů](./dataset-datatable-dataview/defining-primary-keys.md).  
  
 Následující příklad kódu ukazuje, jak přidat informace o schématu do **datové sady** pomocí **FillSchema**.  
  
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
  
 Následující příklad kódu ukazuje, jak přidat informace o schématu do **datové sady** pomocí vlastnosti **MissingSchemaAction. AddWithKey** metody **Fill** .  
  
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
  
## <a name="handling-multiple-result-sets"></a>Zpracování více sad výsledků  
 Pokud modul **DataAdapter** narazí na více sad výsledků vrácených z vlastnosti **SelectCommand**, vytvoří v **datové sadě**více tabulek. Tabulkám bude předána přírůstkový výchozí název **tabulky** *N*založený na nule, počínaje **tabulkou** namísto "Table0". Pokud je název tabulky předán jako argument pro metodu **FillSchema** , tabulky budou předány s nulovým přírůstkovým názvem **TableName** *N*, počínaje hodnotou **TableName** namísto "TableName0".  
  
> [!NOTE]
> Pokud je metoda **FillSchema** objektu **objektu OleDbDataAdapter** volána pro příkaz, který vrací více sad výsledků, vrátí se pouze informace o schématu z první sady výsledků dotazu. Při vracení informací o schématu pro více sad výsledků pomocí **objektu OleDbDataAdapter**se doporučuje zadat **MissingSchemaAction** **AddWithKey** a získat informace o schématu při volání **výplně** . Metoda.  
  
## <a name="see-also"></a>Viz také:

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Datové sady, datové tabulky a datová zobrazení](./dataset-datatable-dataview/index.md)
- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
- [Přehled ADO.NET](ado-net-overview.md)

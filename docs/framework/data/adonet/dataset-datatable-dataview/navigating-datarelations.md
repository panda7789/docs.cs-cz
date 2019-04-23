---
title: Navigace v datových relacích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: f4dfccad23bf5d15f5cbd0a33e76a136417e13ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204156"
---
# <a name="navigating-datarelations"></a>Navigace v datových relacích
Jednou z primárních funkcí <xref:System.Data.DataRelation> je umožnit navigace z jednoho <xref:System.Data.DataTable> do jiného v rámci <xref:System.Data.DataSet>. To umožňuje načíst všechny související <xref:System.Data.DataRow> objektů v jednom **DataTable** při jediném **DataRow** z se souvisejícím **DataTable**. Například po vytvoření **DataRelation** mezi tabulku zákazníků a tabulku objednávek, můžete načíst všechny objednávky řádky pro konkrétní zákazníky řádku pomocí **GetChildRows**.  
  
 Následující příklad kódu vytvoří **DataRelation** mezi **zákazníkům** tabulky a **objednávky** tabulku **datovou sadu** a vrátí všechny objednávky pro každého zákazníka.  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 Následující příklad je založen na předchozím příkladu společně týkající se čtyřmi tabulkami a procházení těchto relací. Stejně jako v předchozím příkladu **CustomerID** se vztahuje **zákazníkům** tabulky **objednávky** tabulky. Pro každého zákazníka v **zákazníkům** všechny podřízené řádky v tabulky **objednávky** tabulky jsou určeny, aby mohla vrátit číslo objednávky určitého zákazníka má a jejich **OrderID** hodnoty.  
  
 Rozšířené příkladu také vrátí hodnoty z **OrderDetails** a **produkty** tabulky. **Objednávky** tabulka má vztah k **OrderDetails** tabulky pomocí **OrderID** určit pro jednotlivé objednávky zákazníka, jaké produktů a množství byly seřazeny. Protože **OrderDetails** tabulka obsahuje pouze **ProductID** seřazený produktu **OrderDetails** souvisí s **produkty** pomocí **ProductID** cílem vrátit **ProductName**. V této relaci **produkty** je nadřazená tabulka a **OrderDetails** je podřízená tabulka. V důsledku toho při iterace **OrderDetails** tabulky, **GetParentRow** je volána k získání související **ProductName** hodnotu.  
  
 Všimněte si, že **DataRelation** se vytvoří pro **zákazníkům** a **objednávky** tabulky, není zadána žádná hodnota pro **createConstraints**příznak (výchozí hodnota je **true**). Předpokladem je, že všechny řádky v tabulce **objednávky** tabulka obsahovat **CustomerID** hodnotu, která existuje v nadřazeném prvku **zákazníkům** tabulky. Pokud **CustomerID** existuje v **objednávky** tabulku, která neexistuje v **zákazníkům** tabulky, <xref:System.Data.ForeignKeyConstraint> způsobí vyvolání výjimky.  
  
 Pokud podřízený sloupec může obsahovat hodnoty, které nebude obsahovat nadřazený sloupec, nastavit **createConstraints** příznak **false** při přidávání **DataRelation**. V tomto příkladu **createConstraints** příznak je nastaven na **false** pro **DataRelation** mezi **objednávky** tabulky a  **OrderDetails** tabulky. To umožňuje aplikaci vrátí všechny záznamy z **OrderDetails** tabulky a pouze podmnožinu záznamů z **objednávky** tabulky bez generování událostí výjimky za běhu. Rozšířené ukázka generuje výstup ve formátu.  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 Následující příklad kódu je rozbalený ukázka kde hodnoty z **OrderDetails** a **produkty** tabulky jsou vráceny pomocí pouze podmnožinu záznamů v **objednávky**tabulky se vrací.  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

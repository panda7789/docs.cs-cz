---
title: Navigace DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: c46007fb86a76405fd99d6e943779238d6885aa8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761425"
---
# <a name="navigating-datarelations"></a>Navigace DataRelations
Jeden z primární funkce <xref:System.Data.DataRelation> je umožnit navigační z jednoho <xref:System.Data.DataTable> do jiné v rámci <xref:System.Data.DataSet>. To umožňuje načíst všechny související <xref:System.Data.DataRow> objektů v jednom **DataTable** li zadán jeden **DataRow** z související **DataTable**. Například po navázání **DataRelation** mezi tabulku zákazníků a tabulku objednávky, můžete načíst všechny řádky pořadí pro konkrétního zákazníka řádek pomocí **Metoda GetChildRows**.  
  
 Následující příklad kódu vytvoří **DataRelation** mezi **zákazníci** tabulky a **objednávky** tabulky **datovou sadu** a vrátí všechny objednávky pro každého zákazníka.  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 Další příklad vychází v předchozím příkladu, týkající se čtyři tabulky dohromady a navigace těchto relací. Jako v předchozím příkladu **CustomerID** má vztah **zákazníci** a **objednávky** tabulky. Pro každého zákazníka a to v **zákazníci** tabulky, všechny podřízené řádky v **objednávky** určuje tabulky, aby bylo možné vrátit číslo objednávky konkrétní zákazník má a jejich **OrderID** hodnoty.  
  
 Rozšířené příklad také vrací hodnoty z **Rozpis objednávek** a **produkty** tabulky. **Objednávky** tabulka souvisí s **Rozpis objednávek** tabulky pomocí **OrderID** k určení, pro každou pořadí zákazníka, jaké produktů a množství byly řazení. Protože **Rozpis objednávek** tabulka obsahuje pouze **ProductID** seřazené produktu **Rozpis objednávek** souvisí s **produkty** pomocí **ProductID** cílem vrátit **ProductName**. V této relaci **produkty** tabulka je nadřazený a **pořadí podrobnosti** tabulka je podřízeným. V důsledku toho, když iterace v rámci **Rozpis objednávek** tabulky, **GetParentRow** nazývá se načíst související **ProductName** hodnotu.  
  
 Všimněte si, že pokud **DataRelation** se vytvoří pro **zákazníci** a **objednávky** tabulky, pro není zadaná žádná hodnota **createConstraints**příznak (výchozí hodnota je **true**). Toto předpokládá, že všechny řádky v **objednávky** tabulka mít **CustomerID** hodnotu, která existuje v nadřízeném **zákazníci** tabulky. Pokud **CustomerID** existuje v **objednávky** tabulku, která neexistuje v **zákazníci** tabulky, <xref:System.Data.ForeignKeyConstraint> způsobí, že vyvolání výjimky.  
  
 Když podřízeného sloupce může obsahovat hodnoty, které nadřazený sloupec neobsahuje, nastavte **createConstraints** příznak, který **false** při přidávání **DataRelation**. V příkladu **createConstraints** je příznak nastaven na **false** pro **DataRelation** mezi **objednávky** atabulky **Rozpis objednávek** tabulky. To umožňuje aplikaci zobrazit všechny záznamy z **Rozpis objednávek** tabulky a pouze podmnožinu záznamů z **objednávky** tabulky bez generování událostí výjimky spuštění. Rozšířené ukázka generuje výstupu v následujícím formátu.  
  
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
  
 Následující příklad kódu je rozšířená ukázka kde hodnoty z **Rozpis objednávek** a **produkty** tabulky se vrátí se pouze podmnožinu záznamy v **objednávky**tabulky nebyl vrácen.  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

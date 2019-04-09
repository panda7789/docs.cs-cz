---
title: Datové sady ADO.NET
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: 50e8e8f5e4b3ee2f5a41cb9dad11b5e701135d9e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190935"
---
# <a name="adonet-datasets"></a>Datové sady ADO.NET
<xref:System.Data.DataSet> Centrální podporuje odpojen, je objekt distribuovaných dat scénáře s [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. **Datovou sadu** rezidentní reprezentace dat, která poskytuje relační konzistentní programovací model bez ohledu na zdroj dat je. Je možné s několika a odlišných zdrojů dat, s daty XML nebo ke správě dat místní aplikace. **Datovou sadu** představuje ucelenou sadu dat, včetně souvisejících tabulek, omezení a relace mezi tabulkami. Je vidět na následujícím obrázku **datovou sadu** objektový model.  
  
 ![ADO.Net graphic](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Model objektu DataSet  
  
 Metody a objektů v **datovou sadu** jsou konzistentní s těmi v modelu relační databáze.  
  
 **Datovou sadu** můžete také zachovat a znovu načíst jeho obsah ve formátu XML a její schéma jako jazyk (XSD) schématu definice schématu XML. Další informace najdete v tématu [použití XML v datové sadě](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **Datovou sadu** obsahuje kolekci nula nebo více tabulek reprezentována <xref:System.Data.DataTable> objekty. <xref:System.Data.DataTableCollection> Obsahuje všechny **DataTable** objekty v **datovou sadu**.  
  
 A **DataTable** je definována v <xref:System.Data> obor názvů a představuje jednu tabulku dat rezidentní. Obsahuje kolekci sloupců reprezentované <xref:System.Data.DataColumnCollection>a omezení reprezentována <xref:System.Data.ConstraintCollection>, které společně definují schéma tabulky. A **DataTable** obsahuje také kolekci řádků reprezentována <xref:System.Data.DataRowCollection>, který obsahuje data v tabulce. Spolu s aktuálním stavu <xref:System.Data.DataRow> zachová svůj aktuální a původní verze identifikovat změny hodnot uložených na řádku.  
  
## <a name="the-dataview-class"></a>DataView – třída  
 A <xref:System.Data.DataView> vám umožní vytvářet různá zobrazení dat uložených v <xref:System.Data.DataTable>, funkce, která se často používá v aplikacích datové vazby. Použití <xref:System.Data.DataView>, můžete zpřístupnit data v tabulce s jiné pořadí řazení a data lze filtrovat podle stavu nebo podle výraz filtru řádků. Další informace najdete v tématu [zobrazení dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 A **datovou sadu** obsahuje vztahy v jeho <xref:System.Data.DataRelationCollection> objektu. Vztah, reprezentovaný <xref:System.Data.DataRelation> objektu přiřadí řádky v jedné **DataTable** s řádky v jiném **DataTable**. Relace je obdobou spojení cestu, která mohou existovat mezi sloupce primární a cizí klíče v relační databázi. A **DataRelation** identifikuje odpovídající sloupce v dvě tabulky **datovou sadu**.  
  
 Vztahy povolení navigace z jedné tabulky do jiného **datovou sadu**. Základní elementy **DataRelation** jsou název vztahu, název tabulky se související a souvisejících sloupců v každé tabulce. Relace se dají vytvářet pomocí více než jeden sloupec tak, že zadáte pole <xref:System.Data.DataColumn> objekty jako klíčové sloupce. Když přidáte vztah k <xref:System.Data.DataRelationCollection>, můžete volitelně přidat **UniqueKeyConstraint** a **Objekt ForeignKeyConstraint** vynucovat omezení integrity, když dojde ke změně související sloupec hodnoty.  
  
 Další informace najdete v tématu [přidání datových relací](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 Můžete přejít k vyplnění **datovou sadu** z datový proud XML nebo dokumentu. Můžete použít na datový proud XML nebo dokument, předejte **datovou sadu** data, informace o schématu nebo obojí. Dodané z datový proud XML nebo dokumentu je možné kombinovat s existující data nebo informace o schématu již v **datovou sadu**. Další informace najdete v tématu [použití XML v datové sadě](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 **Datovou sadu**, **DataTable**, a **DataColumn** mají **ExtendedProperties** vlastnost. **ExtendedProperties** je **PropertyCollection třídy DirectoryEntry** umístění vlastní informace, například příkaz SELECT, který se použil k vygenerování sadu výsledků dotazu nebo při generování data. **ExtendedProperties** přetrvává shromažďování informací o schématu pro **datovou sadu**.  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] poskytuje integrovaný jazyk dotazování funkce pro odpojené data uložená v datové sadě. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] používá standardní [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] syntaxe a poskytuje kontrola syntaxe v době kompilace, psát statické a podporu technologie IntelliSense při použití integrovaného vývojového prostředí sady Visual Studio.  
  
 Další informace najdete v tématu [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

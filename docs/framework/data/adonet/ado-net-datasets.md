---
title: Datové sady
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: 86c14f516ff82e4d9acf7cc3078e04590971a8a1
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980298"
---
# <a name="adonet-datasets"></a>Datové sady ADO.NET
Objekt <xref:System.Data.DataSet> je centrální pro podporu odpojených a distribuovaných datových scénářů pomocí ADO.NET. **Datová sada** je reprezentace dat rezidentního v paměti, která poskytuje konzistentní relační programovací model bez ohledu na zdroj dat. Dá se použít s více a různými zdroji dat, s daty XML nebo pro správu místních dat do aplikace. **Datová sada** představuje kompletní sadu dat, včetně souvisejících tabulek, omezení a vztahů mezi tabulkami. Na následujícím obrázku je znázorněn objektový model **DataSet** .  
  
 ![Obrázek ADO.Net](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Objektový model DataSet  
  
 Metody a objekty v **datové sadě** jsou konzistentní s hodnotami v modelu relační databáze.  
  
 **Datová sada** může také uchovávat a znovu načíst obsah jako XML a jeho schéma jako schéma XML Schema Definition Language (XSD). Další informace naleznete v tématu [using XML in a DataSet](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>Tabulka DataTableCollection  
 **Datová sada** ADO.NET obsahuje kolekci nula nebo více tabulek reprezentovaných <xref:System.Data.DataTable> objekty. <xref:System.Data.DataTableCollection> obsahuje všechny objekty **DataTable** v **datové sadě**.  
  
 **DataTable** je definována v oboru názvů <xref:System.Data> a představuje jednu tabulku rezidentních dat v paměti. Obsahuje kolekci sloupců reprezentovaných <xref:System.Data.DataColumnCollection>a omezení reprezentovaná <xref:System.Data.ConstraintCollection>, která společně definují schéma tabulky. **DataTable** také obsahuje kolekci řádků reprezentovaných <xref:System.Data.DataRowCollection>, která obsahuje data v tabulce. Spolu se svým aktuálním stavem <xref:System.Data.DataRow> uchová jak aktuální, tak původní verzi, aby bylo možné identifikovat změny hodnot uložených na řádku.  
  
## <a name="the-dataview-class"></a>Třída DataView  
 <xref:System.Data.DataView> umožňuje vytvářet různá zobrazení dat uložených v <xref:System.Data.DataTable>, což je funkce, která se často používá v aplikacích pro datovou vazbu. Pomocí <xref:System.Data.DataView>můžete vystavit data v tabulce s různými objednávkami řazení a data můžete filtrovat podle stavu řádku nebo podle výrazu filtru. Další informace naleznete v tématu [DataViews](./dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 **Datová sada** obsahuje relace ve svém objektu <xref:System.Data.DataRelationCollection>. Vztah reprezentovaný objektem <xref:System.Data.DataRelation> přidružuje řádky v jednom objektu **DataTable** k řádkům v jiném **objektu DataTable**. Vztah je podobný cestě spojení, která může existovat mezi sloupci primárního a cizího klíče v relační databázi. **DataRelation** identifikuje vyhovující sloupce ve dvou tabulkách **datové sady**.  
  
 Relace umožňují navigaci z jedné tabulky do druhé v **datové sadě**. Základními prvky **DataRelation** jsou název vztahu, Název souvisejících tabulek a související sloupce v každé tabulce. Relace lze vytvořit s více než jedním sloupcem na tabulku zadáním pole <xref:System.Data.DataColumn> objekty jako klíčové sloupce. Když přidáte relaci do <xref:System.Data.DataRelationCollection>, můžete volitelně přidat **UniqueKeyConstraint** a **Objekt ForeignKeyConstraint** , aby se vynutila omezení integrity při změně souvisejících hodnot sloupců.  
  
 Další informace najdete v tématu [Přidání datových vztahů](./dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 **Datovou sadu** můžete vyplnit z datového proudu XML nebo dokumentu. Pomocí datového proudu nebo dokumentu XML můžete zadat **datovou sadu** , údaje o schématu nebo obojí. Informace předávané z datového proudu XML nebo dokumentu lze kombinovat s existujícími informacemi nebo schématy, které jsou již v **datové sadě**přítomny. Další informace naleznete v tématu [using XML in a DataSet](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 Všechny **datové sady**, **DataTable**a **DataColumn** mají vlastnost **ExtendedProperties** . **ExtendedProperties** je **vlastnostcollection** , kde lze umístit vlastní informace, například příkaz SELECT, který byl použit k vygenerování sady výsledků, nebo čas, kdy byla data vygenerována. Kolekce **ExtendedProperties** je trvale uložena s informacemi o schématu pro **datovou sadu**.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 LINQ to DataSet poskytuje možnosti dotazování integrované v jazyce pro odpojená data uložená v datové sadě. LINQ to DataSet používá standardní syntaxi LINQ a poskytuje kontrolu syntaxe v době kompilace, statické typování a podporu technologie IntelliSense při použití integrovaného vývojového prostředí (IDE) sady Visual Studio.  
  
 Další informace najdete v tématu [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](ado-net-overview.md)
- [Datové sady, datové tabulky a datová zobrazení](./dataset-datatable-dataview/index.md)
- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)

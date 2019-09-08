---
title: Datové sady ADO.NET
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: acbe5a549539a77d63332687486cbe8744592f8b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786984"
---
# <a name="adonet-datasets"></a>Datové sady ADO.NET
<xref:System.Data.DataSet> Objekt je centrální pro podporu odpojených a distribuovaných datových scénářů pomocí ADO.NET. **Datová sada** je reprezentace dat rezidentního v paměti, která poskytuje konzistentní relační programovací model bez ohledu na zdroj dat. Dá se použít s více a různými zdroji dat, s daty XML nebo pro správu místních dat do aplikace. **Datová sada** představuje kompletní sadu dat, včetně souvisejících tabulek, omezení a vztahů mezi tabulkami. Na následujícím obrázku je znázorněn objektový model **DataSet** .  
  
 ![Obrázek ADO.NET](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Objektový model DataSet  
  
 Metody a objekty v **datové sadě** jsou konzistentní s hodnotami v modelu relační databáze.  
  
 **Datová sada** může také uchovávat a znovu načíst obsah jako XML a jeho schéma jako schéma XML Schema Definition Language (XSD). Další informace naleznete v tématu [using XML in a DataSet](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>Tabulka DataTableCollection  
 **Datová sada** ADO.NET obsahuje kolekci nula nebo více tabulek reprezentovaných <xref:System.Data.DataTable> objekty. Obsahuje všechny objekty **DataTable** v **datové sadě.** <xref:System.Data.DataTableCollection>  
  
 V <xref:System.Data> oboru názvů je definován **objekt DataTable** a představuje jednu tabulku rezidentních dat v paměti. Obsahuje kolekci sloupců reprezentovaných <xref:System.Data.DataColumnCollection>a omezení reprezentovaná <xref:System.Data.ConstraintCollection>, která společně definují schéma tabulky. **DataTable** také obsahuje kolekci řádků reprezentovaných <xref:System.Data.DataRowCollection>, která obsahuje data v tabulce. Spolu s jeho aktuálním stavem si <xref:System.Data.DataRow> uchová jak aktuální, tak původní verzi, aby bylo možné identifikovat změny hodnot uložených na řádku.  
  
## <a name="the-dataview-class"></a>Třída DataView  
 Umožňuje vytvářet různá zobrazení dat uložených <xref:System.Data.DataTable>v nástroji, což je funkce, která se často používá v aplikacích s datovou vazbou. <xref:System.Data.DataView> <xref:System.Data.DataView>Pomocí můžete vystavit data v tabulce s různými objednávkami řazení a data můžete filtrovat podle stavu řádku nebo podle výrazu filtru. Další informace naleznete v tématu [DataViews](./dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 **Datová sada** obsahuje relace ve svém <xref:System.Data.DataRelationCollection> objektu. Vztah reprezentovaný <xref:System.Data.DataRelation> objektem, přidruží řádky v jednom objektu **DataTable** k řádkům v jiném **objektu DataTable**. Vztah je podobný cestě spojení, která může existovat mezi sloupci primárního a cizího klíče v relační databázi. **DataRelation** identifikuje vyhovující sloupce ve dvou tabulkách **datové sady**.  
  
 Relace umožňují navigaci z jedné tabulky do druhé v **datové sadě**. Základními prvky **DataRelation** jsou název vztahu, Název souvisejících tabulek a související sloupce v každé tabulce. Relace lze vytvořit s více než jedním sloupcem na tabulku zadáním pole <xref:System.Data.DataColumn> objektů jako klíčových sloupců. Když přidáte relaci do <xref:System.Data.DataRelationCollection>, můžete volitelně přidat **UniqueKeyConstraint** a **Objekt ForeignKeyConstraint** pro vynutit omezení integrity při změně v souvisejících hodnotách sloupce.  
  
 Další informace najdete v tématu [Přidání datových vztahů](./dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 **Datovou sadu** můžete vyplnit z datového proudu XML nebo dokumentu. Pomocí datového proudu nebo dokumentu XML můžete zadat **datovou sadu** , údaje o schématu nebo obojí. Informace předávané z datového proudu XML nebo dokumentu lze kombinovat s existujícími informacemi nebo schématy, které jsou již v **datové sadě**přítomny. Další informace naleznete v tématu [using XML in a DataSet](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 Všechny **datové sady**, **DataTable**a **DataColumn** mají vlastnost **ExtendedProperties** . **ExtendedProperties** je **vlastnostcollection** , kde lze umístit vlastní informace, například příkaz SELECT, který byl použit k vygenerování sady výsledků, nebo čas, kdy byla data vygenerována. Kolekce **ExtendedProperties** je trvale uložena s informacemi o schématu pro **datovou sadu**.  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 LINQ to DataSet poskytuje možnosti dotazování integrované v jazyce pro odpojená data uložená v datové sadě. LINQ to DataSet používá standardní [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] syntaxi a poskytuje kontrolu syntaxe v době kompilace, statické typování a podporu technologie IntelliSense při použití integrovaného vývojového prostředí (IDE) sady Visual Studio.  
  
 Další informace najdete v tématu [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](ado-net-overview.md)
- [Datové sady, datové tabulky a datová zobrazení](./dataset-datatable-dataview/index.md)
- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)

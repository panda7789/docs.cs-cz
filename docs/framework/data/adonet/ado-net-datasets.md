---
title: "Datové sady ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b117b8b75cd4b90f3689fa535b0afbac0ca00fdc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="adonet-datasets"></a>Datové sady ADO.NET
<xref:System.Data.DataSet> Objekt centrální podpory připojen, distribuci dat scénáře s [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. **Datovou sadu** rezidentní znázornění dat, která zajišťuje konzistentní relační programovací model bez ohledu na zdroj dat je. Dá použít s několika a různé zdroje dat, s daty XML nebo spravovat data místní aplikace. **Datovou sadu** představuje kompletní sadu dat, včetně tabulky v relaci, omezení a relace mezi tabulkami. Následující obrázek ukazuje **datovou sadu** objektový model.  
  
 ![Obrázek ADO.Net](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Datová sada objektový Model  
  
 Metody a objektů v **datovou sadu** jsou konzistentní s těmi ve model relační databáze.  
  
 **Datovou sadu** můžete také zachovat a znovu načíst jeho obsah ve formátu XML a schématem jako schématu XML schéma definition language (XSD). Další informace najdete v tématu [pomocí XML v datové sadě](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **Datovou sadu** obsahuje kolekci nula nebo více tabulek reprezentována <xref:System.Data.DataTable> objekty. <xref:System.Data.DataTableCollection> Obsahuje všechny **DataTable** objekty v **datovou sadu**.  
  
 A **DataTable** je definována v <xref:System.Data> obor názvů a představuje jednu tabulku dat rezidentní v paměti. Obsahuje kolekci sloupců reprezentované <xref:System.Data.DataColumnCollection>a omezení reprezentována <xref:System.Data.ConstraintCollection>, které společně definuje schéma tabulky. A **DataTable** také obsahuje kolekci řádků reprezentována <xref:System.Data.DataRowCollection>, který obsahuje data v tabulce. Spolu s aktuálním stavu <xref:System.Data.DataRow> uchovává její aktuální a původní verze identifikovat změny hodnotami uloženými v řádku.  
  
## <a name="the-dataview-class"></a>DataView – třída  
 A <xref:System.Data.DataView> umožňuje vytvářet různá zobrazení dat uložených v <xref:System.Data.DataTable>, funkci, která se často používá v aplikacích datové vazby. Použití <xref:System.Data.DataView>, můžou zpřístupnit data v tabulce s různým řazením a data lze filtrovat podle řádku stavu nebo podle výraz filtru. Další informace najdete v tématu [DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 A **datovou sadu** obsahuje vztahy v jeho <xref:System.Data.DataRelationCollection> objektu. Vztah, reprezentována <xref:System.Data.DataRelation> objekt, partnerů řádky v jednom **DataTable** s řádky v jiném **DataTable**. Relace je obdobou k připojení k cestě, která mohou existovat mezi primární a cizí klíče v relační databázi. A **DataRelation** identifikuje odpovídající sloupce v obou tabulkách **datovou sadu**.  
  
 Vztahy povolení navigace z jedné tabulky do druhého v **datovou sadu**. Základní prvky **DataRelation** jsou název relace, název tabulky se související a související sloupce v každé tabulce. Relace je možné sestavit s více než jeden sloupec pro tabulku zadáním pole <xref:System.Data.DataColumn> objekty jako klíčové sloupce. Když přidáte vztah k <xref:System.Data.DataRelationCollection>, můžete přidat **UniqueKeyConstraint** a **vlastnosti ForeignKeyConstraint** vynutit omezení integrity, při změně sloupec v relaci hodnoty.  
  
 Další informace najdete v tématu [přidání DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 Můžete vyplnit **datovou sadu** z datového proudu XML nebo dokumentu. Datový proud XML nebo dokument můžete použít k poskytování k **datovou sadu** data, informace o schématu nebo obojí. Informací získaných z datového proudu XML nebo dokumentů mohou být kombinovány s existující data nebo informace o schématu již existuje v **datovou sadu**. Další informace najdete v tématu [pomocí XML v datové sadě](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 **Datovou sadu**, **DataTable**, a **DataColumn** všechny mají **ExtendedProperties** vlastnost. **ExtendedProperties** je **PropertyCollection** umístění vlastní informace, například příkaz SELECT, který byl použit ke generování sadu výsledků dotazu nebo čas, kdy byl vygenerován data. **ExtendedProperties** kolekce jako trvalý, s informace o schématu **datovou sadu**.  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]poskytuje language-integrated dotazování možnosti pro odpojené data uložená v datové sadě. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]používá standardní [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] syntaxe a poskytuje kontrolu syntaxe kompilaci, statické zadáním a podporu technologie IntelliSense, při použití [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] IDE.  
  
 Další informace najdete v tématu [LINQ na DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

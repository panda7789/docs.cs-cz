---
title: Datové tabulky
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: f6509400d7f6633749155f778e3ba58ec6c27ec2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879994"
---
# <a name="datatables"></a>Datové tabulky
A <xref:System.Data.DataSet> se skládá z kolekce tabulky, relace a omezení. V ADO.NET <xref:System.Data.DataTable> objekty se používají k vyjádření tabulky v **datovou sadu**. A **DataTable** představuje jedné tabulky v paměti relačních dat; je pro místní data. Aplikace založené na sítě, ve kterém se nachází, ale je možné importovat ze zdroje dat, jako je například Microsoft SQL serveru pomocí **DataAdapter** Další informace najdete v tématu [naplnění datové sady z adaptéru dat](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .  
  
 **DataTable** třídy je členem skupiny **System.Data** oboru názvů v knihovně tříd rozhraní .NET Framework. Můžete vytvořit a použít **DataTable** samostatně nebo jako člen **datovou sadu**, a **DataTable** objektů lze také použít ve spojení s jinými objekty rozhraní .NET Framework včetně <xref:System.Data.DataView>. Přístup ke kolekci tabulek v **datovou sadu** prostřednictvím **tabulky** vlastnost **datovou sadu** objektu.  
  
 Schéma a struktura tabulky je reprezentován sloupců a omezení. Definujete schéma **DataTable** pomocí <xref:System.Data.DataColumn> objekty stejně jako <xref:System.Data.ForeignKeyConstraint> a <xref:System.Data.UniqueConstraint> objekty. Sloupce v tabulce můžete mapovat na sloupce ve zdroji dat, obsahují vypočítané hodnoty z výrazů, automaticky zvýšit jejich hodnoty nebo obsahovat hodnoty primárního klíče.  
  
 Kromě schématu **DataTable** musí také mít řádků, který má obsahovat a pořadí data. <xref:System.Data.DataRow> Třída reprezentuje skutečná data obsažená v tabulce. Můžete použít **DataRow** a její vlastnosti a metody pro načtení, vyhodnocení a manipulaci s daty v tabulce. Jak získávat přístup a měnit data v řádku, **DataRow** objektu udržuje jeho aktuální a původní stav.  
  
 Můžete vytvořit nadřazené podřízené relace mezi tabulkami pomocí jednoho nebo více souvisejících sloupců v tabulkách. Vytvoření vztahu mezi **DataTable** objektů pomocí <xref:System.Data.DataRelation>. **DataRelation** objekty je pak možné vrátit související podřízené a nadřazené řádky konkrétního řádku. Další informace najdete v tématu [přidání datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 Vysvětluje, jak vytvořit **DataTable** a přidejte ji tak **datovou sadu**.  
  
 [Definice schématu datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 Poskytuje informace o vytváření a používání **DataColumn** objekty a omezení.  
  
 [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 Vysvětluje, jak přidat, upravit a odstranit data v tabulce. Vysvětluje způsob používání **DataTable** událostí k prozkoumání změny dat v tabulce.  
  
 [Zpracování událostí datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 Poskytuje informace o událostech, které jsou k dispozici pro použití se službou **DataTable**, včetně události při změně hodnoty sloupců a řádků jsou přidána nebo odstraněna.  
  
## <a name="related-sections"></a>Související oddíly  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 Popisuje ADO.NET architektura a komponenty a jejich použití pro přístup k existujícím zdrojům dat a spravovat data aplikací.  
  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Poskytuje informace o ADO.NET **datovou sadu** včetně vytvoření relace mezi tabulkami.  
  
 <xref:System.Data.Constraint>  
 Poskytuje referenční informace o **omezení** objektu.  
  
 <xref:System.Data.DataColumn>  
 Poskytuje referenční informace o **DataColumn** objektu.  
  
 <xref:System.Data.DataSet>  
 Poskytuje referenční informace o **datovou sadu** objektu.  
  
 <xref:System.Data.DataTable>  
 Poskytuje referenční informace o **DataTable** objektu.  
  
 [Přehled knihovny tříd](../../../../../docs/standard/class-library-overview.md)  
 Najdete zde přehled knihovny tříd rozhraní .NET Framework, včetně **systému** obor názvů a také svůj obor názvů druhé úrovně **System.Data**.  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

---
title: Datové tabulky
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: 12255f738dea0a4713389e599468d1a7fab67d23
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784703"
---
# <a name="datatables"></a>Datové tabulky
A <xref:System.Data.DataSet> se skládá z kolekce tabulek, relací a omezení. V ADO.NET <xref:System.Data.DataTable> objekty slouží k reprezentaci tabulek v **datové sadě**. **DataTable** představuje jednu tabulku relačních dat v paměti; data jsou místní pro. Síť založená na síti, ve které se nachází, ale je možné ji naplnit ze zdroje dat, jako je například Microsoft SQL Server použití třídy **DataAdapter** Další informace naleznete v tématu [naplnění datové sady z objektu DataAdapter](../populating-a-dataset-from-a-dataadapter.md).  
  
 Třída **DataTable** je členem oboru názvů **System. data** v knihovně tříd .NET Framework. Můžete vytvořit a použít **DataTable** nezávisle nebo jako člen **datové sady**a objekty **DataTable** lze také použít ve spojení s jinými objekty <xref:System.Data.DataView>.NET Framework, včetně. Ke kolekci tabulek v **datové sadě** získáte přístup pomocí vlastnosti **Tables** objektu **DataSet** .  
  
 Schéma nebo struktura tabulky jsou reprezentovány sloupci a omezeními. Definujete schéma **objektu DataTable** pomocí <xref:System.Data.DataColumn> <xref:System.Data.ForeignKeyConstraint> objektů i objektů a <xref:System.Data.UniqueConstraint> . Sloupce v tabulce lze namapovat na sloupce ve zdroji dat, obsahovat počítané hodnoty z výrazů, automaticky zvyšovat jejich hodnoty nebo obsahovat hodnoty primárního klíče.  
  
 Kromě schématu musí mít **DataTable** také řádky, které mají obsahovat a seřadit data. <xref:System.Data.DataRow> Třída představuje skutečná data obsažená v tabulce. K načtení, vyhodnocení a manipulaci s daty v tabulce můžete použít vlastnost **DataRow** a její vlastnosti a metody. Při přístupu a změně dat v rámci řádku objekt **DataRow** udržuje jak aktuální, tak původní stav.  
  
 Relace nadřazený-podřízený mezi tabulkami můžete vytvořit pomocí jednoho nebo více souvisejících sloupců v tabulkách. Můžete vytvořit relaci mezi objekty **DataTable** pomocí <xref:System.Data.DataRelation>. Objekty **DataRelation** se pak dají použít k vrácení souvisejících podřízených nebo nadřazených řádků konkrétního řádku. Další informace najdete v tématu [Přidání datových vztahů](adding-datarelations.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření datové tabulky](creating-a-datatable.md)  
 Vysvětluje, jak vytvořit **objekt DataTable** a přidat ho do **datové sady**.  
  
 [Definice schématu datové tabulky](datatable-schema-definition.md)  
 Poskytuje informace o vytváření a používání objektů a omezení **DataColumns** .  
  
 [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)  
 Vysvětluje, jak přidat, upravit a odstranit data v tabulce. Vysvětluje, jak použít události **DataTable** k prohlédnutí změn dat v tabulce.  
  
 [Zpracování událostí datové tabulky](handling-datatable-events.md)  
 Poskytuje informace o událostech, které jsou k dispozici pro použití s **DataTable**, včetně událostí při změně hodnot sloupce a přidání nebo odstranění řádků.  
  
## <a name="related-sections"></a>Související oddíly  
 [ADO.NET](../index.md)  
 Popisuje architekturu a komponenty ADO.NET a jejich použití pro přístup k existujícím zdrojům dat a správě dat aplikace.  
  
 [Datové sady, datové tabulky a datová zobrazení](index.md)  
 Poskytuje informace o **datové sadě** ADO.NET, včetně postupu při vytváření relací mezi tabulkami.  
  
 <xref:System.Data.Constraint>  
 Poskytuje referenční informace o objektu **omezení** .  
  
 <xref:System.Data.DataColumn>  
 Poskytuje referenční informace o objektu **DataColumn** .  
  
 <xref:System.Data.DataSet>  
 Poskytuje referenční informace o objektu **DataSet** .  
  
 <xref:System.Data.DataTable>  
 Poskytuje referenční informace o objektu **DataTable** .  
  
 [Přehled knihovny tříd](../../../../standard/class-library-overview.md)  
 Poskytuje přehled knihovny tříd .NET Framework, včetně oboru názvů **System** , a také oboru názvů na druhé úrovni, **System. data**.  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../ado-net-overview.md)

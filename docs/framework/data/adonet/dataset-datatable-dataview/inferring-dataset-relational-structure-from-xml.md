---
title: Odvození relační struktury datové sady z XML
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: f5cbbcd148f13a630398e870124803d482f63698
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587645"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>Odvození relační struktury datové sady z XML
Relační struktury nebo schématu, nástroje <xref:System.Data.DataSet> se skládá z tabulky, sloupce, omezení a vztahy. Při načítání <xref:System.Data.DataSet> ze souboru XML, můžete předem definovaná schématu, ale mohou být vytvořeny, explicitně nebo prostřednictvím odvození z XML načítán. Další informace o načítání schématu a obsah <xref:System.Data.DataSet> ze souboru XML, naleznete v tématu [načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) a [načítání informace schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
 Pokud schéma <xref:System.Data.DataSet> se vytváří ze souboru XML, upřednostňovanou metodou je nutné explicitně zadat pomocí buď schéma XML definice jazyk (XSD) schématu (jak je popsáno v [odvozování relační struktury datové sady ze schématu XML (XSD) ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)) nebo XML Data snižuje (XDR). Pokud není k dispozici v jazyce XML schématu žádné schéma XML nebo XDR schéma <xref:System.Data.DataSet> lze odvodit z struktura XML elementů a atributů.  
  
 Tato část popisuje pravidla pro <xref:System.Data.DataSet> odvození schématu zobrazením elementů XML a atributy a jejich strukturu a výsledné odvodit <xref:System.Data.DataSet> schématu.  
  
 Ne všechny atributy v dokumentu XML musí být součástí procesu odvození. Namespace kvalifikovaný atributy mohou zahrnovat metadata, která jsou důležité pro dokument XML, ale nikoli pro <xref:System.Data.DataSet> schématu. Pomocí <xref:System.Data.DataSet.InferXmlSchema%2A>, můžete určit obory názvů mají ignorovat během procesu odvození. Další informace najdete v tématu [načítání informace schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Souhrn procesu odvození schématu datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/summary-of-the-dataset-schema-inference-process.md)  
 Poskytuje podrobný přehled pravidla pro odvození schématu <xref:System.Data.DataSet> ze souboru XML.  
  
 [Odvozování tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)  
 Popisuje elementy XML, které jsou odvozeny jako tabulky v <xref:System.Data.DataSet>.  
  
 [Odvozování sloupců](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-columns.md)  
 Popisuje elementy XML a atributy, které jsou odvozeny jako sloupce tabulky.  
  
 [Odvozování relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-relationships.md)  
 Popisuje <xref:System.Data.DataRelation> a <xref:System.Data.ForeignKeyConstraint> objekty vytvořené pro vnořený, odvozené tabulky.  
  
 [Odvození textu elementu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-element-text.md)  
 Popisuje sloupce, které jsou vytvořeny pro text v elementů XML a vysvětluje, kdy text v elementů XML je ignorován.  
  
 [Odvození omezení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inference-limitations.md)  
 Tento článek popisuje omezení pro odvození schématu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Popisuje, jak <xref:System.Data.DataSet> objekt pracuje s daty XML.  
  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační struktury nebo schématu, <xref:System.Data.DataSet> , který je vytvořen z jazyk (XSD) schématu definice schématu XML.  
  
 [Přehled ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 Popisuje ADO.NET architektura a komponenty a jejich použití pro přístup k existujícím zdrojům dat a spravovat data aplikací.  
  
## <a name="see-also"></a>Viz také:
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

---
title: Odvození relační strukturu datové sady z XML
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: 6ded5e893ccca973f8be5f070f68d9d8c7e09678
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>Odvození relační strukturu datové sady z XML
Relační struktura nebo schéma z <xref:System.Data.DataSet> se skládá z tabulky, sloupce, omezení a vztahů. Při načítání <xref:System.Data.DataSet> ze souboru XML, můžete předem definovaná schématu, ale mohou být vytvořeny, explicitně nebo prostřednictvím odvozená z XML načítá. Další informace o načítání schématu a obsah <xref:System.Data.DataSet> ze souboru XML, najdete v části [načítání datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) a [načítání datovou sadu informace o schématu z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
 Pokud schéma <xref:System.Data.DataSet> se vytváří z XML, je upřednostňovanou metodou k explicitnímu zadání schématu pomocí schématu XML definice jazyka (XSD) (jak je popsáno v [odvozování relační strukturu datové sady z schématu XML (XSD) ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)) nebo XML Data snížit (XDR). Pokud je k dispozici v souboru XML, schéma žádné schéma schématu XML nebo XDR <xref:System.Data.DataSet> lze odvodit z strukturu XML elementů a atributů.  
  
 Tato část popisuje pravidla pro <xref:System.Data.DataSet> odvození schématu zobrazením elementů XML a atributy a jejich struktura a výsledná odvodit <xref:System.Data.DataSet> schématu.  
  
 Všechny atributy, které se nachází v dokumentu XML by měl být součástí procesu odvození. Namespace kvalifikovaný atributy mohou zahrnovat metadata, která je důležité pro dokument XML, ale ne <xref:System.Data.DataSet> schématu. Pomocí <xref:System.Data.DataSet.InferXmlSchema%2A>, můžete určit obory názvů, který se má ignorovat během procesu odvození. Další informace najdete v tématu [načítání datovou sadu informace o schématu z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Souhrn procesu odvození schématu datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/summary-of-the-dataset-schema-inference-process.md)  
 Poskytuje shrnutí pravidel pro odvození schéma <xref:System.Data.DataSet> ze souboru XML.  
  
 [Odvozování tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)  
 Popisuje elementy XML, které jsou odvozené jako tabulky <xref:System.Data.DataSet>.  
  
 [Odvozování sloupců](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-columns.md)  
 Popisuje elementy XML a atributů, které jsou odvozené jako sloupců tabulky.  
  
 [Odvozování relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-relationships.md)  
 Popisuje <xref:System.Data.DataRelation> a <xref:System.Data.ForeignKeyConstraint> objekty vytvořené pro vnořený, odvozené tabulky.  
  
 [Odvození textu elementu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-element-text.md)  
 Popisuje sloupce, které jsou vytvořené pro text v kódu XML elementů a vysvětluje, pokud je text v elementů XML ignoruje.  
  
 [Odvození omezení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inference-limitations.md)  
 Popisuje omezení odvození schématu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Popisuje, jak <xref:System.Data.DataSet> objekt komunikuje se službou XML data.  
  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační struktura nebo schéma z <xref:System.Data.DataSet> vytvořený ze schématu XML definition language (XSD) schématu.  
  
 [Přehled ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 Popisuje technologie ADO.NET architektura a komponenty a jak je používat pro přístup k existující zdroje dat a spravovat data aplikací.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

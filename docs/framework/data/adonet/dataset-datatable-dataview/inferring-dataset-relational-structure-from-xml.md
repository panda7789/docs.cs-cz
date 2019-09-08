---
title: Odvození relační struktury datové sady z XML
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: 1c8325d7ed52fea7397a7b5aa8744bdfa90b2c6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785315"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>Odvození relační struktury datové sady z XML
Relační struktura neboli schéma <xref:System.Data.DataSet> se skládá z tabulek, sloupců, omezení a vztahů. Při načítání <xref:System.Data.DataSet> z kódu XML může být schéma předdefinovaný nebo může být vytvořeno buď explicitně, nebo prostřednictvím odvození, od načtení XML. Další informace o načtení schématu a obsahu <xref:System.Data.DataSet> z jazyka XML naleznete v tématu [načtení datové sady z XML](loading-a-dataset-from-xml.md) a [načtení informací o schématu datové sady z XML](loading-dataset-schema-information-from-xml.md).  
  
 Je-li schéma <xref:System.Data.DataSet> z kódu XML vytvořeno, upřednostňovanou metodou je explicitní určení schématu pomocí jazyka XSD (XML Schema Definition Language) (jak je popsáno v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)) nebo XML – zmenšeno na data (XDR). Pokud není v kódu XML k dispozici žádné schéma XML nebo schéma XDR, schéma <xref:System.Data.DataSet> lze odvodit ze struktury elementů XML a atributů.  
  
 Tato část popisuje pravidla pro <xref:System.Data.DataSet> odvození schématu zobrazením elementů XML a atributů a jejich struktury a výsledného <xref:System.Data.DataSet> odvozeného schématu.  
  
 Ne všechny atributy, které jsou k dispozici v dokumentu XML, by měly být zahrnuty v procesu odvození. Atributy kvalifikované pro obor názvů můžou zahrnovat metadata, která jsou důležitá pro dokument XML, ale ne <xref:System.Data.DataSet> pro schéma. Pomocí <xref:System.Data.DataSet.InferXmlSchema%2A>můžete zadat obory názvů, které budou ignorovány během procesu odvození. Další informace naleznete v tématu [načítání informací o schématu datové sady z XML](loading-dataset-schema-information-from-xml.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Souhrn procesu odvození schématu datové sady](summary-of-the-dataset-schema-inference-process.md)  
 Poskytuje souhrnný přehled pravidel pro odvození schématu <xref:System.Data.DataSet> z XML.  
  
 [Odvozování tabulek](inferring-tables.md)  
 Popisuje elementy XML, které jsou odvozeny jako tabulky v <xref:System.Data.DataSet>.  
  
 [Odvozování sloupců](inferring-columns.md)  
 Popisuje elementy XML a atributy, které jsou odvozeny jako sloupce tabulky.  
  
 [Odvozování relací](inferring-relationships.md)  
 Popisuje objekty <xref:System.Data.ForeignKeyConstraint> a vytvořené pro vnořené a odvozené tabulky. <xref:System.Data.DataRelation>  
  
 [Odvození textu elementu](inferring-element-text.md)  
 Popisuje sloupce, které jsou vytvořeny pro text v prvcích XML a vysvětluje, kdy se text v prvcích XML ignoruje.  
  
 [Odvození omezení](inference-limitations.md)  
 Popisuje omezení odvození schématu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Použití XML v datové sadě](using-xml-in-a-dataset.md)  
 Popisuje, <xref:System.Data.DataSet> jak objekt komunikuje s daty XML.  
  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační strukturu neboli schéma <xref:System.Data.DataSet> , které je vytvořeno ze schématu XSD (XML Schema Definition Language).  
  
 [Přehled ADO.NET](../ado-net-overview.md)  
 Popisuje architekturu a komponenty ADO.NET a jejich použití pro přístup k existujícím zdrojům dat a správě dat aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../ado-net-overview.md)

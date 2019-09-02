---
title: Použití XML v datové sadě
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: ba68f0fbe84a9877596ddfefd56f71a5889cf8de
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203138"
---
# <a name="using-xml-in-a-dataset"></a>Použití XML v datové sadě
Pomocí ADO.NET můžete vyplnit <xref:System.Data.DataSet> datový proud XML nebo dokument. Datový proud XML nebo dokument můžete použít k poskytnutí <xref:System.Data.DataSet> dat, informací o schématu nebo obojího. Informace poskytnuté z datového proudu XML nebo dokumentu lze kombinovat se stávajícími informacemi o schématu, které <xref:System.Data.DataSet>již existují v nástroji.  
  
 ADO.NET také umožňuje vytvořit reprezentaci <xref:System.Data.DataSet>XML s a bez jejího schématu, aby bylo možné <xref:System.Data.DataSet> přenést přenos přes protokol HTTP pro použití jinou aplikací nebo platformou podporující XML. V jazyce XML reprezentace <xref:System.Data.DataSet>a jsou data zapsána do XML a schématu, pokud je vložena do reprezentace, jsou zapsána pomocí jazyka XML Schema Definition Language (XSD). Schéma XML a XML poskytují pohodlný formát pro přenos obsahu <xref:System.Data.DataSet> a ze vzdálených klientů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [DiffGrams](diffgrams.md)  
 Poskytuje podrobné informace o formátu DiffGram, formátu XML, který se používá ke čtení a zápisu obsahu <xref:System.Data.DataSet>.  
  
 [Načtení datové sady z XML](loading-a-dataset-from-xml.md)  
 Popisuje různé možnosti, které je <xref:System.Data.DataSet> třeba vzít v úvahu při načítání obsahu z dokumentu XML.  
  
 [Kopírování obsahu datové sady jako dat XML](writing-dataset-contents-as-xml-data.md)  
 Popisuje, jak vygenerovat obsah a <xref:System.Data.DataSet> jako data XML, a různé možnosti formátu XML, které můžete použít.  
  
 [Načtení informací o schématu datové sady z XML](loading-dataset-schema-information-from-xml.md)  
 Popisuje metody používané pro načtení schématu <xref:System.Data.DataSet> z kódu XML. <xref:System.Data.DataSet>  
  
 [Zápis informací o schématu datové sady jako XSD](writing-dataset-schema-information-as-xsd.md)  
 Popisuje použití pro schéma XML a způsob, jak jej vygenerovat <xref:System.Data.DataSet>.  
  
 [Synchronizace datové sady a datového dokumentu XML](dataset-and-xmldatadocument-synchronization.md)  
 Popisuje možnosti dostupné v .NET Framework synchronního přístupu k relačním i hierarchickým zobrazením jedné sady dat a ukazuje, jak vytvořit synchronní vztah mezi <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument>a a.  
  
 [Vnoření datových relací](nesting-datarelations.md)  
 Popisuje důležitost vnořených <xref:System.Data.DataRelation> objektů, které představují obsah a <xref:System.Data.DataSet> jako data XML, a popisuje, jak je vytvořit.  
  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační strukturu neboli schéma <xref:System.Data.DataSet> , které je vytvořeno ze schématu XML.  
  
 [Odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md)  
 Popisuje výslednou relační strukturu neboli schéma <xref:System.Data.DataSet> , které je vytvořeno při odvození z prvků XML.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled ADO.NET](../ado-net-overview.md)  
 Popisuje architekturu a komponenty ADO.NET a jejich použití pro přístup k existujícím zdrojům dat a také ke správě aplikačních dat.  
  
## <a name="see-also"></a>Viz také:

- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

---
title: Použití XML v datové sadě
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: 9e586ff0c6f28dd5919bc8b1bc640389a5cad610
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087416"
---
# <a name="using-xml-in-a-dataset"></a>Použití XML v datové sadě
Pomocí ADO.NET můžete přejít k vyplnění <xref:System.Data.DataSet> z datový proud XML nebo dokumentu. Můžete použít na datový proud XML nebo dokument, předejte <xref:System.Data.DataSet> data, informace o schématu nebo obojí. Dodané z datový proud XML nebo dokumentu je možné kombinovat s existující data nebo informace o schématu již v <xref:System.Data.DataSet>.  
  
 ADO.NET také umožňuje vytvořit reprezentaci v jazyce XML <xref:System.Data.DataSet>, s nebo bez jeho schématu, aby bylo možné přenést <xref:System.Data.DataSet> přes HTTP používají jiné aplikace nebo XML povolené platformy. V reprezentaci XML <xref:System.Data.DataSet>, data je napsána v XML a schéma, pokud je zahrnuty vložené v reprezentaci, je zapsáno s použitím jazyka pro definici schématu XML (XSD). XML a schéma XML poskytují pohodlný formát pro přenos obsahu <xref:System.Data.DataSet> do a ze vzdálených klientů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 Poskytuje podrobné informace o formát DiffGram formátu XML ke čtení a zápis obsahu <xref:System.Data.DataSet>.  
  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 Tento článek popisuje různé možnosti, které je třeba zvážit při načítání obsahu <xref:System.Data.DataSet> z dokumentu XML.  
  
 [Kopírování obsahu datové sady jako dat XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 Popisuje, jak generovat obsah <xref:System.Data.DataSet> jako XML data a různé možnosti formátu XML, můžete použít.  
  
 [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 Tento článek popisuje <xref:System.Data.DataSet> metody používané k načtení schématu <xref:System.Data.DataSet> ze souboru XML.  
  
 [Zápis informací o schématu datové sady jako XSD](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 Popisuje využití pro schématu XML a tom, jak vygenerovat z <xref:System.Data.DataSet>.  
  
 [Synchronizace datové sady a datového dokumentu XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 Tento článek popisuje funkce dostupné v rozhraní .NET Framework synchronní přístup k relačních a hierarchických zobrazení jedné sady dat a ukazuje, jak vytvořit relaci mezi synchronním <xref:System.Data.DataSet> a <xref:System.Xml.XmlDataDocument>.  
  
 [Vnoření datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 Tento článek popisuje význam vnořené <xref:System.Data.DataRelation> objekty při vyjadřování obsah <xref:System.Data.DataSet> jako data XML a popisuje, jak je vytvářet.  
  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační struktury nebo schématu, <xref:System.Data.DataSet> , který je vytvořen ze schématu XML.  
  
 [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 Popisuje výsledný relační struktury nebo schématu, <xref:System.Data.DataSet> , který je vytvořen při odvodit z elementů XML.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 Popisuje ADO.NET architektura a komponenty a jejich použití pro přístup k stávajících zdrojů dat stejně jako ke správě dat aplikací.  
  
## <a name="see-also"></a>Viz také:

- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

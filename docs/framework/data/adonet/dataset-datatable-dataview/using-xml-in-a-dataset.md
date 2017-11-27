---
title: "Pomocí XML v datové sadě"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 28c1668dcb9678b65db62c0040adcd116221b92e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-xml-in-a-dataset"></a>Pomocí XML v datové sadě
S ADO.NET, můžete vyplnit <xref:System.Data.DataSet> z datového proudu XML nebo dokumentu. Datový proud XML nebo dokument můžete použít k poskytování k <xref:System.Data.DataSet> data, informace o schématu nebo obojí. Informací získaných z datového proudu XML nebo dokumentů mohou být kombinovány s existující data nebo informace o schématu již existuje v <xref:System.Data.DataSet>.  
  
 ADO.NET umožňuje taky vytvořit reprezentaci XML <xref:System.Data.DataSet>, s nebo bez jeho schématu, aby bylo možné přenosu <xref:System.Data.DataSet> přes HTTP pro použití jiná aplikace nebo platformu XML povolen. V XML reprezentaci <xref:System.Data.DataSet>, budou data zapsána v kódu XML a schématu, pokud je součástí vložený v rámci reprezentace je zapsán pomocí jazyka definice schématu XML (XSD). XML a schématu XML poskytují pohodlný formát pro přenos obsahu <xref:System.Data.DataSet> do a ze vzdálených klientů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 Poskytuje podrobné informace o formátu DiffGram formátu XML, který používá ke čtení a zápis obsahu <xref:System.Data.DataSet>.  
  
 [Načítání datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 Popisuje různé možnosti, které je třeba zvážit při načítání obsahu <xref:System.Data.DataSet> z dokumentu XML.  
  
 [Zápis obsah datovou sadu jako XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 Popisuje, jak vygenerovat obsah <xref:System.Data.DataSet> jako XML data a můžete použít různé možnosti formátu XML.  
  
 [Načítání informací o schématu sady dat z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 Popisuje <xref:System.Data.DataSet> metod používaných k načtení schématu <xref:System.Data.DataSet> ze souboru XML.  
  
 [Zápis informací o schématu datovou sadu jako XSD](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 Popisuje využití pro schéma XML a jak vygenerovat z <xref:System.Data.DataSet>.  
  
 [Datové sady a XmlDataDocument synchronizace](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 Popisuje funkce dostupné v rozhraní .NET Framework synchronní přístupu k relačních i hierarchické zobrazení jednu sadu dat a ukazuje, jak vytvořit synchronní relaci mezi tabulkou <xref:System.Data.DataSet> a <xref:System.Xml.XmlDataDocument>.  
  
 [DataRelations vnoření](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 Popisuje význam vnořené <xref:System.Data.DataRelation> objekty při představující obsah <xref:System.Data.DataSet> jako data XML a popisuje, jak k jejich vytvoření.  
  
 [Odvozování relační strukturu datové sady z schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační struktura nebo schéma z <xref:System.Data.DataSet> vytvořený z schématu XML.  
  
 [Odvození relační strukturu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 Popisuje výsledné relační struktura nebo schéma z <xref:System.Data.DataSet> vytvořený při odvodit z elementů XML.  
  
## <a name="related-sections"></a>Související oddíly  
 [ADO.NET – přehled](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 Popisuje technologie ADO.NET architektura a komponenty a jak je používat pro přístup k existující zdroje dat. také jako ke správě dat aplikací.  
  
## <a name="see-also"></a>Viz také  
 [Datové sady, DataTables a DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

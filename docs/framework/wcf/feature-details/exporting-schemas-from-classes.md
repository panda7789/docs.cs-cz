---
title: "Export schémat ze tříd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, schema import and export
- schemas [WCF], exporting from classes
- schemas [WCF]
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: bb57b962-70c1-45a9-93d5-e721e340a13f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01e841e76c4a6cf06169113422921367d671ea98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="exporting-schemas-from-classes"></a>Export schémat ze tříd
Chcete-li vygenerovat schématu XML definition language (XSD) schémat ze třídy, které se používají v datovém modelu kontrakt, použijte <xref:System.Runtime.Serialization.XsdDataContractExporter> třídy. Toto téma popisuje proces pro vytváření schémat.  
  
## <a name="the-export-process"></a>Proces exportu  
 Proces exportu schématu začíná jeden nebo více typů a vytváří <xref:System.Xml.Schema.XmlSchemaSet> projekce XML z těchto typů, který popisuje.  
  
 `XmlSchemaSet` Je součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]na schéma objektu modelu (SOM) představující sadu schématu XSD dokumenty. Vytvářet dokumenty XSD z `XmlSchemaSet`, použít kolekci schémat ze <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost `XmlSchemaSet` třídy. Potom serializovat každý <xref:System.Xml.Schema.XmlSchema> pomocí <xref:System.Xml.Serialization.XmlSerializer>.  
  
#### <a name="to-export-schemas"></a>Export schémat  
  
1.  Vytvoření instance <xref:System.Runtime.Serialization.XsdDataContractExporter>.  
  
2.  Volitelné. Předat <xref:System.Xml.Schema.XmlSchemaSet> v konstruktoru. V takovém případě je schéma vygenerovaných během exportu schématu přidány do tohoto <xref:System.Xml.Schema.XmlSchemaSet> instanci místo počínaje prázdné <xref:System.Xml.Schema.XmlSchemaSet>.  
  
3.  Volitelné. Volání jednoho z <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> metody. Metoda určuje, zda je možné exportovat zadaného typu. Metoda má stejné přetížení, jako `Export` metoda v dalším kroku.  
  
4.  Volání jednoho z <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metody. Existují tři přetížení trvá <xref:System.Type>, <xref:System.Collections.Generic.List%601> z `Type` objekty, nebo <xref:System.Collections.Generic.List%601> z <xref:System.Reflection.Assembly> objekty. V posledním případě se exportují všechny typy v dané sestavení.  
  
     Více volá, aby se `Export` metody za následek více položek, který se přidává do stejné `XmlSchemaSet`. Typ nevygenerovala do `XmlSchemaSet` Pokud zde již existuje. Proto volání `Export` víckrát na stejný `XsdDataContractExporter` je vhodnější vytváření více instancí `XsdDataContractExporter` třídy. Tím je zabráněno typy duplicitní schémat generování.  
  
    > [!NOTE]
    >  Pokud dojde k selhání během exportu, `XmlSchemaSet` bude v nepředvídatelném stavu.  
  
5.  Přístup <xref:System.Xml.Schema.XmlSchemaSet> prostřednictvím <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> vlastnost.  
  
## <a name="export-options"></a>Možnosti exportu  
 Můžete nastavit <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> vlastnost <xref:System.Runtime.Serialization.XsdDataContractExporter> na instanci systému <xref:System.Runtime.Serialization.ExportOptions> třídy ovládat různé aspekty procesu exportu. Konkrétně můžete nastavit následující možnosti:  
  
-   <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Tato kolekce `Type` představuje známé typy pro typy, která je exportována. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).) Tyto známé typy exportují se na každý `Export` volání navíc k typům předaný `Export` metoda.  
  
-   <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. <xref:System.Runtime.Serialization.IDataContractSurrogate> Můžete zadat pomocí této vlastnosti, která bude přizpůsobení procesu exportu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Ve výchozím nastavení se používá žádné náhradní.  
  
## <a name="helper-methods"></a>Pomocné metody  
 Kromě jeho primární roli exportu schématu `XsdDataContractExporter` poskytuje několik užitečné pomocné metody, které poskytují informace o typech. Mezi ně patří:  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A>Metoda. Tato metoda přebírá `Type` a vrátí <xref:System.Xml.XmlQualifiedName> představující název kořenového elementu a obor názvů, který se použije, pokud se tento typ serializovat jako kořenový objekt.  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A>Metoda. Tato metoda přebírá `Type` a vrátí <xref:System.Xml.XmlQualifiedName> představující název typ schématu XSD, který se použije, pokud byly exportovány tento typ schématu. Pro <xref:System.Xml.Serialization.IXmlSerializable> typy reprezentován jako anonymní typy ve schématu, tato metoda vrátí `null`.  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A>Metoda. Tato metoda funguje jenom s <xref:System.Xml.Serialization.IXmlSerializable> typy, které jsou reprezentovány jako anonymní typy ve schématu a vrátí `null` pro všechny ostatní typy. Anonymní typy, tato metoda vrátí hodnotu <xref:System.Xml.Schema.XmlSchemaType> představující danou `Type`.  
  
 Možnosti exportu mít vliv na všechny z těchto metod.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 [Import a export schémat](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)  
 [Import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)

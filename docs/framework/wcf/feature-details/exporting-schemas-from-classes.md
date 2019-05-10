---
title: Export schémat ze tříd
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, schema import and export
- schemas [WCF], exporting from classes
- schemas [WCF]
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: bb57b962-70c1-45a9-93d5-e721e340a13f
ms.openlocfilehash: c5c11ebf87f68a87c410c87fd860ba58f4f63a35
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587588"
---
# <a name="exporting-schemas-from-classes"></a>Export schémat ze tříd
Ke generování schématu XML definice jazyk (XSD) schémat ze tříd, které se používají v datovém modelu smlouvy, použijte <xref:System.Runtime.Serialization.XsdDataContractExporter> třídy. Toto téma popisuje proces pro vytvoření schémat.  
  
## <a name="the-export-process"></a>Proces exportu  
 Proces exportu schématu začíná na jeden nebo více typů a vytváří <xref:System.Xml.Schema.XmlSchemaSet> , který popisuje projekce XML z těchto typů.  
  
 `XmlSchemaSet` Je součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]od schématu objektu modelu (SOM), který představuje sadu dokumentů schématu XSD. Vytvoření dokumentů XSD z `XmlSchemaSet`, použít kolekci schémat ze <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost `XmlSchemaSet` třídy. Potom serializovat každý <xref:System.Xml.Schema.XmlSchema> pomocí <xref:System.Xml.Serialization.XmlSerializer>.  
  
#### <a name="to-export-schemas"></a>Export schémat  
  
1. Vytvoření instance <xref:System.Runtime.Serialization.XsdDataContractExporter>.  
  
2. Volitelné. Předávání <xref:System.Xml.Schema.XmlSchemaSet> v konstruktoru. V takovém případě schématu generovaném během exportu schématu se přidá k tomuto <xref:System.Xml.Schema.XmlSchemaSet> instanci místo počínaje prázdnou hodnotu <xref:System.Xml.Schema.XmlSchemaSet>.  
  
3. Volitelné. Volání jednoho z <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> metody. Metoda určuje, zda zadaný typ je možné exportovat. Tato metoda má stejný přetížení, jako `Export` metoda v dalším kroku.  
  
4. Volání jednoho z <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metody. Existují tři přetížení s ohledem <xref:System.Type>, <xref:System.Collections.Generic.List%601> z `Type` objektů, nebo <xref:System.Collections.Generic.List%601> z <xref:System.Reflection.Assembly> objekty. V posledním případě jsou exportovány všechny typy v dané sestavení.  
  
     Více volání `Export` metody za následek více položek, které se přidávají do stejné `XmlSchemaSet`. Typ negeneruje do `XmlSchemaSet` Pokud již existuje. Proto volání `Export` více než jednou ve stejném `XsdDataContractExporter` je vhodnější než vytvoření více instancí `XsdDataContractExporter` třídy. Tím se vyhnete duplicitního schématu typy nefunkční.  
  
    > [!NOTE]
    >  Pokud dojde k selhání během exportu, `XmlSchemaSet` bude v nepředvídatelném stavu.  
  
5. Přístup <xref:System.Xml.Schema.XmlSchemaSet> prostřednictvím <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> vlastnost.  
  
## <a name="export-options"></a>Možnosti exportu  
 Můžete nastavit <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> vlastnost <xref:System.Runtime.Serialization.XsdDataContractExporter> do instance <xref:System.Runtime.Serialization.ExportOptions> třídy ovládat různé aspekty procesu exportu. Konkrétně můžete nastavit následující možnosti:  
  
- <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Tato kolekce `Type` představuje známých typů pro exportované typy. (Další informace najdete v tématu [známé typy kontraktů dat.](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).) Tyto známé typy jsou exportovány na každý `Export` volání kromě typů předávaného `Export` metody.  
  
- <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. <xref:System.Runtime.Serialization.IDataContractSurrogate> Může být poskytnuta prostřednictvím této vlastnosti, které se přizpůsobí procesu exportu. Další informace najdete v tématu [náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Ve výchozím nastavení je použít žádné náhrady.  
  
## <a name="helper-methods"></a>Pomocné metody  
 Kromě jeho primární role export schématu `XsdDataContractExporter` poskytuje několik užitečné pomocné metody, které poskytují informace o typech. Zde jsou některé z nich:  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A> Metoda. Tato metoda přebírá `Type` a vrátí <xref:System.Xml.XmlQualifiedName> , která představuje název kořenového elementu a obor názvů, který se použije, pokud tento typ byl serializován jako kořenový objekt.  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A> Metoda. Tato metoda přebírá `Type` a vrátí <xref:System.Xml.XmlQualifiedName> , která představuje název typu schématu XSD, který se použije, pokud bylo exportováno tento typ schématu. Pro <xref:System.Xml.Serialization.IXmlSerializable> typy reprezentovaná jako anonymní typy ve schématu, tato metoda vrátí `null`.  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A> Metoda. Tato metoda se dá použít jenom s <xref:System.Xml.Serialization.IXmlSerializable> typy, které jsou reprezentovány jako anonymní typy ve schématu a vrátí `null` pro všechny ostatní typy. Anonymní typy, tato metoda vrátí hodnotu <xref:System.Xml.Schema.XmlSchemaType> , která představuje daný `Type`.  
  
 Možnosti exportu ovlivňují všechny tyto metody.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Import a export schémat](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [Import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)

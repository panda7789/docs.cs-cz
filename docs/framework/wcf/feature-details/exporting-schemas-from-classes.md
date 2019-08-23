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
ms.openlocfilehash: 3db3cc1c529ab40bf775c06a5128e4dabf3c8a56
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963655"
---
# <a name="exporting-schemas-from-classes"></a>Export schémat ze tříd
Pro generování schémat XML Schema Definition Language (XSD) z tříd, které jsou používány v modelu kontraktu dat, použijte <xref:System.Runtime.Serialization.XsdDataContractExporter> třídu. Toto téma popisuje proces vytváření schémat.  
  
## <a name="the-export-process"></a>Proces exportu  
 Proces exportu schématu začíná jedním nebo více typy a vytvoří <xref:System.Xml.Schema.XmlSchemaSet> , který popisuje projekci XML těchto typů.  
  
 `XmlSchemaSet` Je součástí modelu objektu schématu .NET Framework (SOM), který představuje sadu dokumentů schématu XSD. Chcete-li vytvořit dokumenty XSD `XmlSchemaSet`z objektu, použijte kolekci schémat <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> z vlastnosti `XmlSchemaSet` třídy. Pak každý <xref:System.Xml.Schema.XmlSchema> objekt serializovat <xref:System.Xml.Serialization.XmlSerializer>pomocí.  
  
#### <a name="to-export-schemas"></a>Export schémat  
  
1. Vytvořte instanci <xref:System.Runtime.Serialization.XsdDataContractExporter>.  
  
2. Volitelný parametr. <xref:System.Xml.Schema.XmlSchemaSet> Předat v konstruktoru. V tomto případě se schéma vygenerované během exportu schématu přidá do této <xref:System.Xml.Schema.XmlSchemaSet> instance místo začátku s prázdným <xref:System.Xml.Schema.XmlSchemaSet>řetězcem.  
  
3. Volitelný parametr. Zavolejte jednu z <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> metod. Metoda určuje, zda lze určený typ exportovat. Metoda má stejná přetížení jako `Export` metoda v dalším kroku.  
  
4. Zavolejte jednu z <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metod. <xref:System.Type>Existují tři přetížení přebírající <xref:System.Collections.Generic.List%601> , <xref:System.Collections.Generic.List%601> z `Type` objektů nebo <xref:System.Reflection.Assembly> objektů. V posledním případě jsou exportovány všechny typy ve všech daných sestaveních.  
  
     Více volání `Export` metody má za následek přidání více položek do stejného `XmlSchemaSet`. Typ se negeneruje do, `XmlSchemaSet` Pokud již existuje. Proto je volání `Export` více instancí stejného `XsdDataContractExporter` typu vhodnější pro `XsdDataContractExporter` vytváření více instancí třídy. Tím se vyhnete generování duplicitních typů schémat.  
  
    > [!NOTE]
    > Pokud při exportu dojde k chybě, `XmlSchemaSet` bude v nepředvídatelném stavu.  
  
5. Přístup k <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> vlastnostem.  
  
## <a name="export-options"></a>Možnosti exportu  
 Můžete nastavit <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> vlastnost <xref:System.Runtime.Serialization.XsdDataContractExporter> na instanci <xref:System.Runtime.Serialization.ExportOptions> třídy pro řízení různých aspektů procesu exportu. Konkrétně můžete nastavit následující možnosti:  
  
- <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Tato kolekce `Type` představuje známé typy pro typy, které jsou exportovány. (Další informace najdete v tématu [známé typy kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).) Tyto známé typy jsou exportovány při `Export` každém volání kromě typů předaných `Export` metodě.  
  
- <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. Pomocí této vlastnosti lze přizpůsobit proces exportu. <xref:System.Runtime.Serialization.IDataContractSurrogate> Další informace najdete v tématu [náhrada za kontrakty dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Ve výchozím nastavení se nepoužívá žádná náhrada.  
  
## <a name="helper-methods"></a>Pomocné metody  
 Kromě primární role exportu schématu `XsdDataContractExporter` poskytuje aplikace několik užitečných pomocných metod, které poskytují informace o typech. Zde jsou některé z nich:  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A>Metoda. Tato metoda přijímá `Type` a <xref:System.Xml.XmlQualifiedName> vrátí hodnotu, která představuje název kořenového elementu a obor názvů, který by byl použit, pokud byl tento typ serializován jako kořenový objekt.  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A>Metoda. Tato metoda přijímá `Type` a <xref:System.Xml.XmlQualifiedName> vrátí hodnotu, která představuje název typu schématu XSD, který by byl použit, pokud byl tento typ exportován do schématu. Pro <xref:System.Xml.Serialization.IXmlSerializable> typy reprezentované jako anonymní typy ve schématu vrátí `null`Tato metoda.  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A>Metoda. Tato metoda funguje pouze s <xref:System.Xml.Serialization.IXmlSerializable> typy, které jsou reprezentovány jako anonymní typy ve schématu, `null` a vrátí pro všechny ostatní typy. Pro anonymní typy Tato metoda vrátí hodnotu <xref:System.Xml.Schema.XmlSchemaType> , která představuje dané. `Type`  
  
 Možnosti exportu mají vliv na všechny tyto metody.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Import a export schémat](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [Import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)

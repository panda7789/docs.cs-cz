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
ms.openlocfilehash: d356450af8ce6690e2142f3487e153bcde095324
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595515"
---
# <a name="exporting-schemas-from-classes"></a>Export schémat ze tříd
Pro generování schémat XML Schema Definition Language (XSD) z tříd, které jsou používány v modelu kontraktu dat, použijte <xref:System.Runtime.Serialization.XsdDataContractExporter> třídu. Toto téma popisuje proces vytváření schémat.  
  
## <a name="the-export-process"></a>Proces exportu  
 Proces exportu schématu začíná jedním nebo více typy a vytvoří <xref:System.Xml.Schema.XmlSchemaSet> , který popisuje projekci XML těchto typů.  
  
 `XmlSchemaSet`Je součástí modelu objektu schématu .NET Framework (SOM), který představuje sadu dokumentů schématu XSD. Chcete-li vytvořit dokumenty XSD z objektu `XmlSchemaSet` , použijte kolekci schémat z <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnosti `XmlSchemaSet` třídy. Pak každý <xref:System.Xml.Schema.XmlSchema> objekt serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer> .  
  
#### <a name="to-export-schemas"></a>Export schémat  
  
1. Vytvořte instanci <xref:System.Runtime.Serialization.XsdDataContractExporter>.  
  
2. Nepovinný parametr. Předat <xref:System.Xml.Schema.XmlSchemaSet> v konstruktoru. V tomto případě se schéma vygenerované během exportu schématu přidá do této <xref:System.Xml.Schema.XmlSchemaSet> instance místo začátku s prázdným řetězcem <xref:System.Xml.Schema.XmlSchemaSet> .  
  
3. Nepovinný parametr. Zavolejte jednu z <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> metod. Metoda určuje, zda lze určený typ exportovat. Metoda má stejná přetížení jako `Export` metoda v dalším kroku.  
  
4. Zavolejte jednu z <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metod. Existují tři přetížení přebírající <xref:System.Type> , <xref:System.Collections.Generic.List%601> z `Type` objektů nebo <xref:System.Collections.Generic.List%601> <xref:System.Reflection.Assembly> objektů. V posledním případě jsou exportovány všechny typy ve všech daných sestaveních.  
  
     Více volání metody má `Export` za následek přidání více položek do stejného `XmlSchemaSet` . Typ se negeneruje do, `XmlSchemaSet` Pokud již existuje. Proto je volání `Export` více `XsdDataContractExporter` instancí stejného typu vhodnější pro vytváření více instancí `XsdDataContractExporter` třídy. Tím se vyhnete generování duplicitních typů schémat.  
  
    > [!NOTE]
    > Pokud při exportu dojde k chybě, `XmlSchemaSet` bude v nepředvídatelném stavu.  
  
5. Přístup k <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> vlastnostem.  
  
## <a name="export-options"></a>Možnosti exportu  
 Můžete nastavit vlastnost na <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> <xref:System.Runtime.Serialization.XsdDataContractExporter> instanci <xref:System.Runtime.Serialization.ExportOptions> třídy pro řízení různých aspektů procesu exportu. Konkrétně můžete nastavit následující možnosti:  
  
- <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Tato kolekce `Type` představuje známé typy pro typy, které jsou exportovány. (Další informace najdete v tématu [známé typy kontraktu dat](data-contract-known-types.md).) Tyto známé typy jsou exportovány při každém `Export` volání kromě typů předaných `Export` metodě.  
  
- <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. <xref:System.Runtime.Serialization.IDataContractSurrogate>Pomocí této vlastnosti lze přizpůsobit proces exportu. Další informace najdete v tématu [náhrada za kontrakty dat](../extending/data-contract-surrogates.md). Ve výchozím nastavení se nepoužívá žádná náhrada.  
  
## <a name="helper-methods"></a>Pomocné metody  
 Kromě primární role exportu schématu `XsdDataContractExporter` poskytuje aplikace několik užitečných pomocných metod, které poskytují informace o typech. Zde jsou některé z nich:  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A>Metoda. Tato metoda přijímá `Type` a vrátí hodnotu <xref:System.Xml.XmlQualifiedName> , která představuje název kořenového elementu a obor názvů, který by byl použit, pokud byl tento typ serializován jako kořenový objekt.  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A>Metoda. Tato metoda přijímá `Type` a vrátí hodnotu <xref:System.Xml.XmlQualifiedName> , která představuje název typu schématu XSD, který by byl použit, pokud byl tento typ exportován do schématu. Pro <xref:System.Xml.Serialization.IXmlSerializable> typy reprezentované jako anonymní typy ve schématu vrátí tato metoda `null` .  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A>Metoda. Tato metoda funguje pouze s <xref:System.Xml.Serialization.IXmlSerializable> typy, které jsou reprezentovány jako anonymní typy ve schématu, a vrátí `null` pro všechny ostatní typy. Pro anonymní typy Tato metoda vrátí hodnotu <xref:System.Xml.Schema.XmlSchemaType> , která představuje dané `Type` .  
  
 Možnosti exportu mají vliv na všechny tyto metody.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Import a export schémat](schema-import-and-export.md)
- [Import schématu pro generování tříd](importing-schema-to-generate-classes.md)

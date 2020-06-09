---
title: Import a export schémat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
ms.openlocfilehash: 942ade69d92d8a213f65a3a2e463b6924e2f986e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590212"
---
# <a name="schema-import-and-export"></a>Import a export schémat
Windows Communication Foundation (WCF) obsahuje nový modul serializace, <xref:System.Runtime.Serialization.DataContractSerializer> . `DataContractSerializer`Překládá mezi objekty .NET Framework a XML (v obou směrech). Kromě samotného serializátoru zahrnuje WCF přidružené mechanismy importu schématu a exportu schématu. *Schéma* je formální, přesný a strojově čitelný popis tvaru XML, který vytváří serializátor nebo ke kterému má deserializovat přístup. WCF používá jako reprezentaci schématu jazyk XSD (konsorcium World Wide Web (W3C) XML Schema Definition Language (XSD), což je široce interoperabilní s mnoha platformami třetích stran.  
  
 Součástí importu schématu je <xref:System.Runtime.Serialization.XsdDataContractImporter> , že převezme dokument schématu XSD a vygeneruje .NET Framework třídy (obvykle třídy kontraktů dat) tak, že serializované formuláře odpovídají danému schématu.  
  
 Například následující fragment schématu:  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 generuje následující typ (mírně jednodušší pro lepší čitelnost).  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Všimněte si, že vygenerovaný typ následuje několik osvědčených postupů pro kontrakty dat (nalezeno v [doporučených postupech: Správa verzí kontraktů dat](../best-practices-data-contract-versioning.md)):  
  
- Typ implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Další informace najdete v tématu [kontrakty dat kompatibilní s dopředné](forward-compatible-data-contracts.md).  
  
- Datové členy jsou implementovány jako veřejné vlastnosti, které zabalí soukromá pole.  
  
- Třída je částečnou třídou a doplňky lze vytvořit bez úprav generovaného kódu.  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>Umožňuje provést zpětný chod – přebírat typy, které jsou serializovatelné pomocí `DataContractSerializer` a generovat dokument schématu XSD.  
  
## <a name="fidelity-is-not-guaranteed"></a>Přesnost není zaručena.  
 Není zaručeno, že schéma nebo typy vytvoří zpáteční cestu s celkovou věrností. (Operace *Round Trip* znamená import schématu pro vytvoření sady tříd a export výsledku pro nové schéma.) Nelze vrátit stejné schéma. V opačném případě není zaručeno zachování přesnosti procesu. (Exportujte typ pro generování schématu a pak importujte typ zpátky. Je nepravděpodobné, že je vrácen stejný typ.)  
  
## <a name="supported-types"></a>Podporované typy  
 Model kontraktu dat podporuje pouze omezené podmnožiny schématu WC3. Jakékoli schéma, které nedodržuje tuto podmnožinu, způsobí výjimku během procesu importu. Například neexistuje žádný způsob, jak určit, aby datový člen kontraktu dat měl být serializován jako atribut XML. Proto schémata, která vyžadují použití atributů XML, nejsou podporována a způsobí během importu výjimky, protože není možné vygenerovat kontrakt dat se správnou projekcí XML.  
  
 Například následující fragment schématu nelze importovat pomocí výchozího nastavení importu.  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 Další informace najdete v tématu [referenční informace o schématu kontraktu dat](data-contract-schema-reference.md). Pokud schéma nevyhovuje pravidlům kontraktu dat, použijte jiný modul serializace. Například <xref:System.Xml.Serialization.XmlSerializer> používá vlastní samostatný mechanismus importu schématu. K dispozici je také zvláštní režim importu, ve kterém je rozsah podporovaného schématu rozbalený. Další informace naleznete v části o generování <xref:System.Xml.Serialization.IXmlSerializable> typů v tématu [Import schématu pro generování tříd](importing-schema-to-generate-classes.md).  
  
 `XsdDataContractExporter`Podporuje všechny typy .NET Framework, které mohou být serializovány pomocí `DataContractSerializer` . Další informace najdete v tématu [typy podporované serializátorem kontraktu dat](types-supported-by-the-data-contract-serializer.md). Všimněte si, že schéma vygenerované pomocí `XsdDataContractExporter` je běžně platná data, která `XsdDataContractImporter` může použít (Pokud <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> se nepoužívá k přizpůsobení schématu).  
  
 Další informace o použití naleznete v <xref:System.Runtime.Serialization.XsdDataContractImporter> tématu [Import schématu pro generování tříd](importing-schema-to-generate-classes.md).  
  
 Další informace o použití naleznete v <xref:System.Runtime.Serialization.XsdDataContractExporter> tématu [Exportování schémat z tříd](exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Import schématu pro generování tříd](importing-schema-to-generate-classes.md)
- [Export schémat ze tříd](exporting-schemas-from-classes.md)

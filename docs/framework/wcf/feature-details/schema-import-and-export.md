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
ms.openlocfilehash: a14ee9e5916133be3979650055cf3e57899a4cca
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591797"
---
# <a name="schema-import-and-export"></a>Import a export schémat
Windows Communication Foundation (WCF) zahrnuje Serializační stroj, <xref:System.Runtime.Serialization.DataContractSerializer>. `DataContractSerializer` Překládá objekty rozhraní .NET Framework a jazyka XML (v obou směrech). Kromě samotného serializátor zahrnuje WCF přidružené schéma importu a exportu mechanismy schématu. *Schéma* je formální, přesné a který je strojově čitelný popis tvar XML, který vytvoří serializátor nebo, který deserializátor může získat přístup. WCF používá World Wide Web Consortium (W3C) schématu XML definice jazyk (XSD) jako její znázornění schématu je široce vzájemná spolupráce s mnoha platforem třetích stran.  
  
 Komponentu import schématu <xref:System.Runtime.Serialization.XsdDataContractImporter>, trvá dokument schématu XSD a generuje rozhraní .NET Framework třídy (obvykle datových tříd smlouvy) tak, aby serializovaná forms odpovídají dané schéma.  
  
 Například následující fragment schématu:  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 generuje následujícího typu (zjednodušené mírně pro lepší čitelnost).  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Všimněte si, že generovaný typ následuje několik osvědčených postupů kontraktu dat (v [osvědčených postupů: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):  
  
- Tento typ implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Další informace najdete v tématu [kontraktů dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
- Datové členy jsou implementovány jako veřejné vlastnosti, které balí privátní pole.  
  
- Třída je částečné třídy a doplňky můžete provést bez úpravy generovaného kódu.  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> Umožňuje opačný – trvat typy, které jsou serializovat pomocí `DataContractSerializer` a generovat dokument schématu XSD.  
  
## <a name="fidelity-is-not-guaranteed"></a>Věrnost není zaručená.  
 Není zaručeno, že schéma nebo typy provést zpáteční cestu věrně celkový počet. (A *odezvy* znamená, že pro import schématu pro vytvoření sadu tříd a export výsledků, znovu vytvořte schéma.) Stejné schéma nesmí vracet. Vrácení procesu není také zaručeno věrnost. (Typ ke generování jeho schématu exportovat a pak importovat typ zpět. Nepravděpodobné, že je vrácena stejného typu.)  
  
## <a name="supported-types"></a>Podporované typy  
 Kontrakt datový model podporuje jenom omezenou podmnožinou WC3 schématu. Žádné schéma, který není v souladu s touto sadou způsobí výjimku během procesu importu. Například neexistuje žádný způsob, jak určit, že datový člen kontraktu dat by měl být serializován jako atribut XML. Proto schémat, které vyžadují použití atributů XML nejsou podporovány a způsobí výjimky během importu, protože je nelze ke generování kontraktu dat s správné projekce XML.  
  
 Například následující fragment schéma nelze importovat pomocí výchozího nastavení pro import.  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 Další informace najdete v tématu [schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Pokud schéma není v souladu s pravidly kontraktu dat, použijte jiný Serializační stroj. Například <xref:System.Xml.Serialization.XmlSerializer> používá vlastní mechanismus samostatné schéma importu. Je také speciální import režim, ve kterém je rozbalená oblast nepodporuje schéma. Další informace najdete v části o generování <xref:System.Xml.Serialization.IXmlSerializable> napíše [import schématu pro generování třídy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 `XsdDataContractExporter` Podporuje všechny typy rozhraní .NET Framework, které mohou serializovat s příznakem `DataContractSerializer`. Další informace najdete v tématu [typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Mějte na paměti Toto schéma vygenerované pomocí `XsdDataContractExporter` je obvykle platný data, která `XsdDataContractImporter` můžete použít (Pokud <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> se používá k úpravě schématu).  
  
 Další informace o používání <xref:System.Runtime.Serialization.XsdDataContractImporter>, naleznete v tématu [import schématu pro generování třídy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Další informace o používání <xref:System.Runtime.Serialization.XsdDataContractExporter>, naleznete v tématu [export schémat ze tříd](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)
- [Export schémat ze tříd](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)

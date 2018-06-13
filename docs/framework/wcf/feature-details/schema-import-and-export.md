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
ms.openlocfilehash: c9bb0d6df362380a37ae3079694ab91e9577741d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497279"
---
# <a name="schema-import-and-export"></a>Import a export schémat
Windows Communication Foundation (WCF) zahrnuje Serializační stroj, <xref:System.Runtime.Serialization.DataContractSerializer>. `DataContractSerializer` Překládá mezi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekty a XML (v obou směrech). Kromě serializátor sám sebe zahrnuje WCF přidružené schéma import a export mechanismy schématu. *Schéma* formální, přesné a strojově čitelným popis obrazec XML, který produkuje serializátor nebo který deserializátor přístup. WCF používá jazyk definice schématu XML World Wide Web Consortium (W3C) (XSD) jako jeho reprezentace schématu, která je široce vzájemná spolupráce s mnoha platformy třetí strany.  
  
 Komponentu import schématu <xref:System.Runtime.Serialization.XsdDataContractImporter>, trvá dokument schématu XSD a generuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] třídy (obvykle třídy kontraktu dat) tak, aby serializovaných formuláře odpovídají daného schématu.  
  
 Například následující fragment schématu:  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 generuje následujícího typu (zjednodušená mírně pro lepší čitelnost).  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Všimněte si, že typ generovaného následuje několik osvědčené postupy kontraktu dat (v nalezen [osvědčené postupy: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):  
  
-   Typ implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Další informace najdete v tématu [kontrakty dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
-   Datové členy jsou implementované jako veřejné vlastnosti, které balí privátním polím.  
  
-   Třída je konkrétní třídu a dodatky můžete provedeny beze změny generovaného kódu.  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> Umožňuje opačný – trvat typů, které jsou serializovat pomocí `DataContractSerializer` a generovat dokument schématu XSD.  
  
## <a name="fidelity-is-not-guaranteed"></a>Přesnost není zaručena.  
 Není zaručeno, že schéma nebo typy provést výměnu zpráv s celkový přesnost. (A *odezvy* znamená pro import schématu vytvořit sadu tříd a exportovat výsledek se znovu vytvořit schéma.) Stejné schéma nemusí být vrácena. Prohodit proces není zaručena také k zachování přesnost. (Typ pro generování schématem exportovat a pak naimportujete typ zpět. Nepravděpodobné, že je vrácen stejného typu.)  
  
## <a name="supported-types"></a>Podporované typy  
 Datový model kontrakt podporuje omezenou podmnožinou WC3 schématu. Žádné schéma, které nejsou v souladu s touto sadou způsobí výjimku během procesu importu. Například neexistuje žádný způsob, jak určit, že se data členem kontraktu dat by měly být serializovány jako atribut XML. Proto schémat, které vyžadují použití atributy XML nejsou podporovány a způsobí, že výjimky během importu, protože není možné vygenerovat kontraktu dat s správné projekce XML.  
  
 Například následující fragment schématu nelze importovat pomocí výchozího nastavení pro import.  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 Další informace najdete v tématu [Přehled schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Pokud schéma nevyhovuje pravidlům kontraktu dat, použijte modul různých serializace. Například <xref:System.Xml.Serialization.XmlSerializer> používá mechanismus import vlastní samostatné schéma. Je taky speciální import režim, ve kterém je rozšířena rozsahu podporované schématu. Další informace najdete v části o generování <xref:System.Xml.Serialization.IXmlSerializable> typy v [import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 `XsdDataContractExporter` Podporuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, které mohou serializovat s příznakem `DataContractSerializer`. Další informace najdete v tématu [typy nepodporuje serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Všimněte si, že schématu generována pomocí `XsdDataContractExporter` je obvykle platný datový, `XsdDataContractImporter` můžete použít (Pokud <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> slouží k přizpůsobení schématu).  
  
 Další informace o používání <xref:System.Runtime.Serialization.XsdDataContractImporter>, najdete v části [import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Další informace o používání <xref:System.Runtime.Serialization.XsdDataContractExporter>, najdete v části [export schémat ze tříd](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 [Import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)  
 [Export schémat ze tříd](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)

---
title: Přehled Modelu objektu schématu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97e2e54c534b30c3c514c9102ded0050fc154b75
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64589792"
---
# <a name="xml-schema-object-model-overview"></a>Přehled Modelu objektu schématu XML
Model objektu schématu (SOM) v rozhraní Microsoft .NET Framework je plnohodnotné rozhraní API, která umožňuje vytvářet, upravovat a ověřit schémata prostřednictvím kódu programu. SOM funguje v dokumentech schémat XML. Podobně jako na způsob, jakým funguje Document Object Model (DOM) v dokumentech XML. Dokumentů schématu XML jsou platné soubory XML, které po načtení do SOM, významu o struktuře a platnosti jiných dokumentů XML, které odpovídají schématu.  
  
 Schéma je dokument XML, který definuje třídu dokumentů XML tak, že zadáte struktura nebo model dokumentů XML pro konkrétní schéma. Schéma určuje omezení u obsahu dokumentů XML a popisuje slovník (pravidla nebo gramatika), který je kompatibilní s dokumenty XML musí dodržovat, aby mohlo být považované za schématu platný s dané schéma. Ověření dokumentu XML je proces, který zajistí, že dokument odpovídá gramatiky určené schéma.  
  
 Níže jsou způsoby SOM rozhraní API v rozhraní .NET Framework umožňuje vytvářet, upravovat a ověřit schémata.  
  
- Načtení a uložení platná schémata do a ze souborů.  
  
- Vytváření pomocí třídy silného typu schémata v paměti.  
  
- Pracovat <xref:System.Xml.Schema.XmlSchemaSet> třída ukládat do mezipaměti, kompilaci a načíst schémata.  
  
- Pracovat <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídy ověřit dokumenty instance XML pomocí schémat.  
  
- Editory sestavení pro vytváření a Správa schémat.  
  
- Dynamicky upravte schéma, které mohou být splněny a uloženy pro použití při ověřování instanci dokumentů XML.  
  
## <a name="the-schema-object-model"></a>Model objektu schématu  
 SOM se skládá z rozsáhlou sadu tříd v <xref:System.Xml.Schema?displayProperty=nameWithType> odpovídající elementy ve schématu XML obor názvů. Například `<xsd:schema>...</xsd:schema>` prvek mapuje na <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> třídy a všechny informace, které mohou být obsaženy v rámci `<xsd:schema/>` elementu lze znázornit pomocí <xref:System.Xml.Schema.XmlSchema> třídy. Podobně `<xsd:element>...</xsd:element>` a `<xsd:attribute>...</xsd:attribute>` mapování elementů na <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> a <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> třídy v uvedeném pořadí. Toto mapování pokračuje pro všechny prvky schématu XML, vytvoření modelu objektu schématu XML v <xref:System.Xml.Schema> obor názvů znázorněn v následujícím diagramu.  
  
 ![Objektový Model System.Xml.Schema](./media/xml-schema-object-model-overview/xml-schema-object-model.gif)  
  
 Další informace o každé třídě <xref:System.Xml.Schema> obor názvů, najdete v článku <xref:System.Xml.Schema> oboru názvů v dokumentaci v knihovně tříd rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také:

- [Čtení ze schémat XML a zápis do nich](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Procházení schémat XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Zahrnutí nebo import schémat XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Informační sada po kompilaci schématu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)

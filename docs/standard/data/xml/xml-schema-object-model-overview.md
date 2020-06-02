---
title: Přehled Modelu objektu schématu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
ms.openlocfilehash: 0358efdcc2e8b86f589eea312d791610da5238db
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290328"
---
# <a name="xml-schema-object-model-overview"></a>Přehled Modelu objektu schématu XML
Model objektu schématu (SOM) v Microsoft .NET Framework je bohatá rozhraní API, které umožňuje programově vytvářet, upravovat a ověřovat schémata. Model SOM pracuje na dokumentech schématu XML podobně jako model DOM (Document Object Model) (DOM) pracuje na dokumentech XML. Dokumenty schématu XML jsou platné soubory XML, které po načtení do modelu SOM přenesou význam pro strukturu a platnost dalších dokumentů XML, které odpovídají schématu.  
  
 Schéma je dokument XML, který definuje třídu dokumentů XML zadáním struktury nebo modelu dokumentů XML pro konkrétní schéma. Schéma určuje omezení obsahu dokumentů XML a popisuje slovní druh (pravidla nebo gramatika), které musí splňovat dokumenty XML, aby bylo možné považovat za schéma – platné s tímto konkrétním schématem. Ověření dokumentu XML je proces, který zajišťuje, že dokument bude v souladu s gramatikou určenou schématem.  
  
 Níže jsou uvedené způsoby, kterými rozhraní API modelu SOM v .NET Framework umožňuje vytváření, úpravy a ověřování schémat.  
  
- Načtení a uložení platných schémat do souborů a ze souborů.  
  
- Vytvářejte schémata v paměti pomocí tříd silného typu.  
  
- Interakci s <xref:System.Xml.Schema.XmlSchemaSet> třídou pro ukládání, kompilování a načítání schémat.  
  
- Interakce s <xref:System.Xml.XmlReader.Create%2A> metodou <xref:System.Xml.XmlReader> třídy pro ověřování dokumentů instance XML proti schématům.  
  
- Editory sestavení pro vytváření a údržbu schémat.  
  
- Dynamicky upravit schéma, které je možné vyhovět a uložit pro použití při ověřování dokumentů instance XML.  
  
## <a name="the-schema-object-model"></a>Model objektu schématu  
 SOM obsahuje rozsáhlou sadu tříd v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů odpovídající prvkům ve schématu XML. Například `<xsd:schema>...</xsd:schema>` element mapuje na <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> třídu a všechny informace, které mohou být obsaženy v rámci `<xsd:schema/>` elementu, mohou být reprezentovány pomocí <xref:System.Xml.Schema.XmlSchema> třídy. Podobně se `<xsd:element>...</xsd:element>` prvky a `<xsd:attribute>...</xsd:attribute>` mapují na <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> třídy a v <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> uvedeném pořadí. Toto mapování pokračuje pro všechny prvky schématu XML vytvoření modelu objektu XML schématu v <xref:System.Xml.Schema> oboru názvů, který je znázorněn v následujícím diagramu.  
  
 ![Model objektu System. XML. Schema](./media/xml-schema-object-model-overview/xml-schema-object-model.gif)  
  
 Další informace o jednotlivých třídách v <xref:System.Xml.Schema> oboru názvů naleznete v <xref:System.Xml.Schema> referenční dokumentaci k oboru názvů v knihovně tříd .NET Framework.  
  
## <a name="see-also"></a>Viz také

- [Čtení ze schémat XML a zápis do nich](reading-and-writing-xml-schemas.md)
- [Sestavování schémat XML](building-xml-schemas.md)
- [Procházení schémat XML](traversing-xml-schemas.md)
- [Úpravy schémat XML](editing-xml-schemas.md)
- [Zahrnutí nebo import schémat XML](including-or-importing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](xmlschemaset-for-schema-compilation.md)
- [Informační sada po kompilaci schématu](post-schema-compilation-infoset.md)

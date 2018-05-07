---
title: Přehled modelu objektů schématu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd25cf94a8a57f20b42f5e14c92b3b43e3378844
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xml-schema-object-model-overview"></a>Přehled modelu objektů schématu XML
Model objektu schématu (SOM) v rozhraní Microsoft .NET Framework je bohatá rozhraní API, která umožňuje vytvářet, upravovat a ověřit schémata prostřednictvím kódu programu. SOM funguje na dokumentech schémat XML podobně jako na způsob, jakým modelu objektu dokumentu (DOM) funguje na dokumenty XML. Dokumentech schémat XML. jsou platné soubory XML, které jednou načtena do SOM, nesou význam o struktuře a platnosti jiných dokumentů XML, která vyhovují schématu.  
  
 Schéma je dokument XML, který definuje třídu dokumentů XML zadáním struktura nebo model dokumentů XML pro konkrétní schématu. Schéma identifikuje omezení u obsah dokumentů XML a popisuje termínů (pravidla nebo gramatika), aby se považovala za schématu platný s dané schéma musí následovat kompatibilní dokumentů XML. Ověření dokumentu XML je proces, který zajistí, že dokument odpovídá gramatika určeného schématu.  
  
 Následují způsoby rozhraní API SOM v rozhraní .NET Framework umožňuje vytvářet, upravovat a ověřit schémata.  
  
-   Načtení a uložte platná schémata do a z soubory.  
  
-   Vytvořte v paměti schémata pomocí třídy silného typu.  
  
-   Komunikovat s <xref:System.Xml.Schema.XmlSchemaSet> třída ukládat do mezipaměti, kompilace a načíst schémat.  
  
-   Komunikovat s <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třída k ověření instance dokumentů XML pomocí schémat.  
  
-   Sestavení editory pro vytváření a Správa schémat.  
  
-   Dynamicky upravte schéma, které mohou být v souladu a uložit pro použití při ověřování dokumentů XML instance.  
  
## <a name="the-schema-object-model"></a>Objektový Model schématu  
 Se skládá z rozsáhlou sadu tříd ve model SOM <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů odpovídající elementům ve schématu XML. Například `<xsd:schema>...</xsd:schema>` se mapuje na element <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> třídy a veškeré informace, které může být obsažený v rámci `<xsd:schema/>` element může být reprezentován pomocí <xref:System.Xml.Schema.XmlSchema> třídy. Podobně `<xsd:element>...</xsd:element>` a `<xsd:attribute>...</xsd:attribute>` elementy mapovat <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> a <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> třídy v uvedeném pořadí. Toto mapování pokračuje pro všechny elementy schématu XML vytváření objektový model schématu XML v <xref:System.Xml.Schema> obor názvů znázorněné na obrázku, který následuje dále.  
  
 ![Objektový Model System.Xml.Schema](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")  
  
 Další informace o každé třídě <xref:System.Xml.Schema> obor názvů, najdete v článku <xref:System.Xml.Schema> obor názvů referenční dokumentaci v knihovně tříd rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také  
 [Čtení ze schémat XML a zápis do nich](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [Sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [Procházení schémat XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [Zahrnutí nebo import schémat XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Informační sada po kompilaci schématu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)

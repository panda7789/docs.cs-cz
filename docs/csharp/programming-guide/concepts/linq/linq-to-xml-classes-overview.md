---
title: Přehled tříd LINQ to XML (C#)
description: Tento článek shrnuje LINQ to XML třídy v jazyce C# v System.Xml. Obor názvů LINQ s krátkým popisem každého.
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 34508f86792cdc7589569b8f12584ffc4379a5fb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165435"
---
# <a name="linq-to-xml-classes-overview-c"></a>Přehled tříd LINQ to XML (C#)
Toto téma poskytuje seznam [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tříd v <xref:System.Xml.Linq> oboru názvů a stručný popis každého z nich.  
  
## <a name="linq-to-xml-classes"></a>Třídy LINQ to XML  
  
### <a name="xattribute-class"></a>XAttribute – třída  
 <xref:System.Xml.Linq.XAttribute>představuje atribut XML. Podrobné informace a příklady naleznete v tématu [XAttribute Class Overview (C#)](./xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>XCData – Třída  
 <xref:System.Xml.Linq.XCData>představuje textový uzel CDATA.  
  
### <a name="xcomment-class"></a>XComment – třída  
 <xref:System.Xml.Linq.XComment>představuje komentář XML.  
  
### <a name="xcontainer-class"></a>XContainer – třída  
 <xref:System.Xml.Linq.XContainer>je abstraktní základní třída pro všechny uzly, které mohou mít podřízené uzly. Následující třídy jsou odvozeny z <xref:System.Xml.Linq.XContainer> třídy:  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>XDeclaration – třída  
 <xref:System.Xml.Linq.XDeclaration>představuje deklaraci XML. Deklarace XML se používá k deklaraci verze XML a kódování dokumentu. Kromě toho deklarace XML určuje, zda je dokument XML samostatný. Pokud je dokument samostatný, neexistují žádná deklarace externích značek, ani externí deklarace DTD, nebo externí parametr entity, na kterou se odkazuje z vnitřní podmnožiny.  
  
### <a name="xdocument-class"></a>XDocument – třída  
 <xref:System.Xml.Linq.XDocument>představuje dokument XML. Podrobné informace a příklady naleznete v tématu [Přehled třídy XDocument (C#)](./xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>XDocumentType – třída  
 <xref:System.Xml.Linq.XDocumentType>představuje definici typu dokumentu XML (DTD).  
  
### <a name="xelement-class"></a>XElement – třída  
 <xref:System.Xml.Linq.XElement>představuje XML element. Podrobné informace a příklady naleznete v tématu [XElement Class Overview (C#)](./xelement-class-overview.md).  
  
### <a name="xname-class"></a>XName – třída  
 <xref:System.Xml.Linq.XName>představuje názvy elementů ( <xref:System.Xml.Linq.XElement> ) a atributů ( <xref:System.Xml.Linq.XAttribute> ). Podrobné informace a příklady naleznete v tématu [Přehled třídy XDocument (C#)](./xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je navržena tak, aby co nejjednodušší názvy XML. V důsledku jejich složitosti se názvy XML často považují za pokročilé téma v XML. Pravděpodobně, Tato složitost nepochází z oborů názvů, které vývojáři pravidelně používají při programování, ale z prefixů oboru názvů. Předpony oboru názvů mohou být užitečné ke zmenšování klávesových úhozů vyžadovaných při zadávání XML nebo ke snazšímu čtení XML. Předpony jsou však často pouze zástupci pro použití plného oboru názvů XML a ve většině případů nejsou požadovány. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zjednodušuje názvy XML tím, že překládá všechny předpony na jejich odpovídající obor názvů XML. Předpony jsou k dispozici, pokud jsou požadovány, prostřednictvím <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> metody.  
  
 V případě potřeby je možné řídit předpony oboru názvů. V některých případech, pokud pracujete s jinými systémy XML, jako jsou XSLT nebo XAML, je nutné řídit předpony oboru názvů. Například pokud máte výraz XPath, který používá předpony oboru názvů a je vložen do šablony stylů XSLT, je nutné zajistit, aby byl dokument XML serializován s předponami oboru názvů, které odpovídají hodnotám používaným ve výrazu XPath.  
  
### <a name="xnamespace-class"></a>XNamespace – třída  
 <xref:System.Xml.Linq.XNamespace>představuje obor názvů pro <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> . Obory názvů jsou součástí <xref:System.Xml.Linq.XName> .  
  
### <a name="xnode-class"></a>XNode – třída  
 <xref:System.Xml.Linq.XNode>je abstraktní třída, která představuje uzly stromu XML. Následující třídy jsou odvozeny z <xref:System.Xml.Linq.XNode> třídy:  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>XNodeDocumentOrderComparer – Třída  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer>poskytuje funkce pro porovnání uzlů pro jejich pořadí dokumentů.  
  
### <a name="xnodeequalitycomparer-class"></a>XNodeEqualityComparer – třída  
 <xref:System.Xml.Linq.XNodeEqualityComparer>poskytuje funkce pro porovnání uzlů pro rovnost hodnot.  
  
### <a name="xobject-class"></a>XObject – třída  
 <xref:System.Xml.Linq.XObject>je abstraktní základní třída <xref:System.Xml.Linq.XNode> a <xref:System.Xml.Linq.XAttribute> . Poskytuje funkce pro anotace a události.  
  
### <a name="xobjectchange-class"></a>XObjectChange – třída  
 <xref:System.Xml.Linq.XObjectChange>Určuje typ události při vyvolání události pro <xref:System.Xml.Linq.XObject> .  
  
### <a name="xobjectchangeeventargs-class"></a>XObjectChangeEventArgs – třída  
 <xref:System.Xml.Linq.XObjectChangeEventArgs>poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> události a <xref:System.Xml.Linq.XObject.Changed> .  
  
### <a name="xprocessinginstruction-class"></a>XProcessingInstruction – třída  
 <xref:System.Xml.Linq.XProcessingInstruction>představuje instrukci pro zpracování XML. Instrukce pro zpracování sděluje informace aplikaci, která zpracovává XML.  
  
### <a name="xtext-class"></a>XText – třída  
 <xref:System.Xml.Linq.XText>představuje textový uzel. Ve většině případů tuto třídu nemusíte používat. Tato třída se primárně používá pro smíšený obsah.  
  
## <a name="see-also"></a>Viz také

- [Přehled programování LINQ to XML (C#)](./linq-to-xml-overview.md)

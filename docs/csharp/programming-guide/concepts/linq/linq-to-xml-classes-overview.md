---
title: LinQ na XML třídy Přehled (C#)
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 55be666fc0db0becb12ec8b525e7fc443536e1df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591882"
---
# <a name="linq-to-xml-classes-overview-c"></a>LinQ na XML třídy Přehled (C#)
Toto téma obsahuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] seznam tříd <xref:System.Xml.Linq> v oboru názvů a krátký popis každého z nich.  
  
## <a name="linq-to-xml-classes"></a>Linq na xml třídy  
  
### <a name="xattribute-class"></a>Třída XAttribute  
 <xref:System.Xml.Linq.XAttribute>představuje atribut XML. Podrobné informace a příklady naleznete v [tématu Přehled třídy XAttribute (C#)](./xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>Třída XCData  
 <xref:System.Xml.Linq.XCData>představuje textový uzel CDATA.  
  
### <a name="xcomment-class"></a>Třída XComment  
 <xref:System.Xml.Linq.XComment>představuje komentář XML.  
  
### <a name="xcontainer-class"></a>Třída XContainer  
 <xref:System.Xml.Linq.XContainer>je abstraktní základní třída pro všechny uzly, které mohou mít podřízené uzly. Následující třídy jsou <xref:System.Xml.Linq.XContainer> odvozeny z třídy:  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>Třída XDeclaration  
 <xref:System.Xml.Linq.XDeclaration>představuje deklaraci XML. Deklarace XML se používá k deklarování verze XML a kódování dokumentu. Deklarace XML navíc určuje, zda je dokument XML samostatný. Pokud je dokument samostatný, neexistují žádné externí deklarace značek, a to buď v externím DTD, nebo v entitě externího parametru, na kterou odkazuje z vnitřní podmnožiny.  
  
### <a name="xdocument-class"></a>Třída XDocument  
 <xref:System.Xml.Linq.XDocument>představuje dokument XML. Podrobné informace a příklady naleznete v [tématu Přehled třídxdocument (C#)](./xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>Třída XDocumentType  
 <xref:System.Xml.Linq.XDocumentType>představuje definici typu dokumentu XML (DTD).  
  
### <a name="xelement-class"></a>Třída XElement  
 <xref:System.Xml.Linq.XElement>představuje element XML. Podrobné informace a příklady naleznete v [tématu Přehled třídy XElement (C#)](./xelement-class-overview.md).  
  
### <a name="xname-class"></a>Třída XName  
 <xref:System.Xml.Linq.XName>představuje názvy<xref:System.Xml.Linq.XElement>prvků ( )<xref:System.Xml.Linq.XAttribute>a atributy ( ). Podrobné informace a příklady naleznete v [tématu Přehled třídxdocument (C#)](./xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je navržen tak, aby názvy XML byly co nejjednodušší. Vzhledem ke své složitosti jsou názvy XML často považovány za pokročilé téma ve formátu XML. Pravděpodobně tato složitost nepochází z oborů názvů, které vývojáři pravidelně používají v programování, ale z předpon oboru názvů. Předpony oboru názvů mohou být užitečné ke snížení úhozů požadovaných při zadávání XML nebo k usnadnění čtení jazyka XML. Předpony jsou však často pouze zástupce pro použití úplného oboru názvů XML a ve většině případů nejsou vyžadovány. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zjednodušuje názvy XML překladem všech předpon do odpovídajícího oboru názvů XML. Předpony jsou k dispozici, pokud <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> jsou požadovány, prostřednictvím metody.  
  
 V případě potřeby je možné řídit předpony oboru názvů. V některých případech, pokud pracujete s jinými systémy XML, jako je například XSLT nebo XAML, je třeba řídit předpony oboru názvů. Pokud například máte výraz XPath, který používá předpony oboru názvů a je vložen do šablony stylů XSLT, musíte se ujistit, že dokument XML je serializován s předčíslími oboru názvů, které odpovídají těm, které jsou použity ve výrazu XPath.  
  
### <a name="xnamespace-class"></a>Třída XNamespace  
 <xref:System.Xml.Linq.XNamespace>představuje obor názvů <xref:System.Xml.Linq.XElement> pro <xref:System.Xml.Linq.XAttribute>nebo . Obory názvů jsou <xref:System.Xml.Linq.XName>součástí aplikace .  
  
### <a name="xnode-class"></a>Třída XNode  
 <xref:System.Xml.Linq.XNode>je abstraktní třída, která představuje uzly stromu XML. Následující třídy jsou <xref:System.Xml.Linq.XNode> odvozeny z třídy:  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>Třída XNodeDocumentOrderComparer  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer>poskytuje funkce pro porovnání uzlů pro jejich pořadí dokumentů.  
  
### <a name="xnodeequalitycomparer-class"></a>Třída XNodeEqualityComparer  
 <xref:System.Xml.Linq.XNodeEqualityComparer>poskytuje funkce pro porovnání uzlů pro rovnost hodnot.  
  
### <a name="xobject-class"></a>Třída XObject  
 <xref:System.Xml.Linq.XObject>je abstraktní základní <xref:System.Xml.Linq.XNode> třída <xref:System.Xml.Linq.XAttribute>a . Poskytuje funkce poznámky a události.  
  
### <a name="xobjectchange-class"></a>Třída XObjectChange  
 <xref:System.Xml.Linq.XObjectChange>určuje typ události, když je událost <xref:System.Xml.Linq.XObject>vyvolána pro .  
  
### <a name="xobjectchangeeventargs-class"></a>Třída XObjectChangeEventArgs  
 <xref:System.Xml.Linq.XObjectChangeEventArgs>poskytuje data <xref:System.Xml.Linq.XObject.Changing> pro <xref:System.Xml.Linq.XObject.Changed> události a.  
  
### <a name="xprocessinginstruction-class"></a>Třída XProcessingInstruction  
 <xref:System.Xml.Linq.XProcessingInstruction>představuje instrukce zpracování XML. Instrukce zpracování sděluje informace aplikaci, která zpracovává XML.  
  
### <a name="xtext-class"></a>Třída XText  
 <xref:System.Xml.Linq.XText>představuje textový uzel. Ve většině případů není třeba používat tuto třídu. Tato třída se používá především pro smíšený obsah.  
  
## <a name="see-also"></a>Viz také

- [Přehled programování LINQ to XML (C#)](./linq-to-xml-overview.md)

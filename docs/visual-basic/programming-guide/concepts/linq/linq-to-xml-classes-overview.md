---
title: Technologie LINQ to XML přehled třídy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
ms.openlocfilehash: dd9e392c1fec86bfb1fe0e0f8bee0cd0c7919fe4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649175"
---
# <a name="linq-to-xml-classes-overview-visual-basic"></a>Technologie LINQ to XML přehled třídy (Visual Basic)
Toto téma obsahuje seznam [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] třídy v <xref:System.Xml.Linq> obor názvů a krátký popis každého.  
  
## <a name="linq-to-xml-classes"></a>Technologie LINQ to XML třídy  
  
### <a name="xattribute-class"></a>XAttribute – třída  
 <xref:System.Xml.Linq.XAttribute> Představuje atribut XML. Podrobné informace a příklady naleznete v tématu [XAttribute přehledu třídy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>XCData – třída  
 <xref:System.Xml.Linq.XCData> představuje uzel text CDATA.  
  
### <a name="xcomment-class"></a>XComment – třída  
 <xref:System.Xml.Linq.XComment> Představuje komentáře jazyka XML.  
  
### <a name="xcontainer-class"></a>XContainer – třída  
 <xref:System.Xml.Linq.XContainer> je abstraktní základní třída pro všechny uzly, které může mít podřízené uzly. Následující třídy odvozovat <xref:System.Xml.Linq.XContainer> třídy:  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>XDeclaration – třída  
 <xref:System.Xml.Linq.XDeclaration> Představuje deklarace XML. Deklarace XML se používá k deklaraci XML verze a kódování dokumentu. Kromě toho deklarace XML určuje, zda je v dokumentu XML samostatné. Pokud dokument je samostatná, neexistují žádné externí značek deklarace v externí DTD nebo v entitu externí parametr na něj odkazovat z vnitřní podmnožiny.  
  
### <a name="xdocument-class"></a>XDocument – třída  
 <xref:System.Xml.Linq.XDocument> Představuje dokument XML. Podrobné informace a příklady naleznete v tématu [XDocument přehledu třídy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>XDocumentType – třída  
 <xref:System.Xml.Linq.XDocumentType> Představuje definici typu dokumentu XML (DTD).  
  
### <a name="xelement-class"></a>XElement – třída  
 <xref:System.Xml.Linq.XElement> Reprezentuje element, XML. Podrobné informace a příklady naleznete v tématu [XElement přehledu třídy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).  
  
### <a name="xname-class"></a>XName – třída  
 <xref:System.Xml.Linq.XName> představuje názvy elementů (<xref:System.Xml.Linq.XElement>) a atributy (<xref:System.Xml.Linq.XAttribute>). Podrobné informace a příklady naleznete v tématu [XDocument přehledu třídy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zajišťují, aby názvy XML maximálně jednoduché. Z důvodu jejich složitost XML názvy jsou často považuje za rozšířená v kódu XML. Tato složitost dodává pravděpodobně, nikoli z oborů názvů, které vývojáři použít pravidelně při programování, ale z předpony oboru názvů. Namespace předpony může být užitečná ke snížení stisknutí kláves potřebné při zadávání XML, nebo k usnadnění XML. Ale předpony jsou často zástupce pro používání úplné obor názvů XML a není nutné ve většině případů. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Vyřešte všechny předpony na jejich odpovídající obor názvů XML zjednodušuje názvů XML. Jsou k dispozici, pokud jsou požadována prostřednictvím předpony <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> metoda.  
  
 Je možné, pokud je to nezbytné, aby se předpony oboru názvů řízení. V některých případech Pokud pracujete s jinými systémy XML, jako je například XSLT nebo XAML, je nutné určit předpony oboru názvů. Například pokud máte výraz XPath, který používá předpony oboru názvů a vložené do šablonu stylů XSLT, je musí ověřit, že je váš dokument XML serializovat s příznakem předpony oboru názvů, které se shodují s těmi, použít ve výrazu XPath.  
  
### <a name="xnamespace-class"></a>XNamespace – třída  
 <xref:System.Xml.Linq.XNamespace> představuje obor názvů pro <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute>. Obory názvů jsou součástí <xref:System.Xml.Linq.XName>.  
  
### <a name="xnode-class"></a>XNode – třída  
 <xref:System.Xml.Linq.XNode> je abstraktní třída, která představuje uzlů stromu XML. Následující třídy odvozovat <xref:System.Xml.Linq.XNode> třídy:  
  
-   <xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>XNodeDocumentOrderComparer – třída  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer> poskytuje funkce pro porovnání uzlů pro jejich dokument pořadí.  
  
### <a name="xnodeequalitycomparer-class"></a>XNodeEqualityComparer – třída  
 <xref:System.Xml.Linq.XNodeEqualityComparer> poskytuje funkce pro porovnání uzlů pro rovnosti hodnoty.  
  
### <a name="xobject-class"></a>XObjektu – třída  
 <xref:System.Xml.Linq.XObject> je abstraktní základní třída z <xref:System.Xml.Linq.XNode> a <xref:System.Xml.Linq.XAttribute>. Nabízí funkce, poznámky a události.  
  
### <a name="xobjectchange-class"></a>XObjectChange – třída  
 <xref:System.Xml.Linq.XObjectChange> Určuje typ události, když událost se vyvolá pro <xref:System.Xml.Linq.XObject>.  
  
### <a name="xobjectchangeeventargs-class"></a>XObjectChangeEventArgs – třída  
 <xref:System.Xml.Linq.XObjectChangeEventArgs> poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed> události.  
  
### <a name="xprocessinginstruction-class"></a>XProcessingInstruction – třída  
 <xref:System.Xml.Linq.XProcessingInstruction> Představuje instrukcí pro zpracování XML. Zpracování instrukcí komunikuje informace, které aplikace, která zpracovává soubor XML.  
  
### <a name="xtext-class"></a>XText – třída  
 <xref:System.Xml.Linq.XText> Představuje uzel text. Ve většině případů není nutné k použití této třídy. Tato třída se používá hlavně pro smíšený obsah.  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to přehled programování v XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

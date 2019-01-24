---
title: Přehled LINQ to XML třídy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
ms.openlocfilehash: 0b95a3f4411e20390962a2eccf28b8cfad4b8e09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570119"
---
# <a name="linq-to-xml-classes-overview-visual-basic"></a>Přehled LINQ to XML třídy (Visual Basic)
Toto téma obsahuje seznam [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tříd v <xref:System.Xml.Linq> obor názvů a krátký popis každého.  
  
## <a name="linq-to-xml-classes"></a>Technologie LINQ to XML tříd  
  
### <a name="xattribute-class"></a>Třídy XAttribute  
 <xref:System.Xml.Linq.XAttribute> představuje atribut XML. Podrobné informace a příklady najdete v tématu [přehled třídy XAttribute (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>Třída XCData  
 <xref:System.Xml.Linq.XCData> reprezentuje textový uzel CDATA.  
  
### <a name="xcomment-class"></a>Třída XComment  
 <xref:System.Xml.Linq.XComment> představuje komentáře XML.  
  
### <a name="xcontainer-class"></a>Třída XContainer  
 <xref:System.Xml.Linq.XContainer> je abstraktní základní třída pro všechny uzly, které mohou obsahovat podřízené uzly. Následující třídy odvozovat <xref:System.Xml.Linq.XContainer> třídy:  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>Třída XDeclaration  
 <xref:System.Xml.Linq.XDeclaration> reprezentuje deklaraci XML. Deklarace XML se používá k deklaraci XML version a kódování dokumentu. Deklarace XML kromě toho určuje, zda je samostatný dokumentu XML. Pokud je dokument samostatné, nejsou žádné deklarací externích značek v externí specifikaci DTD nebo externí parametr entity na něj odkazovat z interní podmnožinu.  
  
### <a name="xdocument-class"></a>Třídy XDocument  
 <xref:System.Xml.Linq.XDocument> Představuje dokumentu XML. Podrobné informace a příklady najdete v tématu [přehled třídy XDocument (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>Třída XDocumentType  
 <xref:System.Xml.Linq.XDocumentType> představuje XML dokumentu typ definice (DTD).  
  
### <a name="xelement-class"></a>Třídy XElement  
 <xref:System.Xml.Linq.XElement> Reprezentuje XML element. Podrobné informace a příklady najdete v tématu [přehled třídy XElement (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).  
  
### <a name="xname-class"></a>Třída XName  
 <xref:System.Xml.Linq.XName> představuje názvy prvků (<xref:System.Xml.Linq.XElement>) a atributy (<xref:System.Xml.Linq.XAttribute>). Podrobné informace a příklady najdete v tématu [přehled třídy XDocument (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je navržená tak, aby tak přímočaré jako možné názvy XML. Z důvodu složitosti názvy XML jsou často považuje za rozšířená ve formátu XML. Tato složitost dodává pravděpodobně, nikoli z obory názvů, které vývojáři pravidelně v programování, ale z předpony oboru názvů. Namespace předpony může být užitečná ke snížení stisknutí kláves vstup XML je vyžadována, nebo pro usnadnění XML. Ale předpony jsou často zástupce pro používání oboru názvů XML úplná a ve většině případů není nutné. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] názvy XML zjednodušuje tím, že všechny předpony, překládá na jejich odpovídající obor názvů XML. Předpony jsou k dispozici, pokud jsou požadována, až <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> metody.  
  
 Je možné, v případě potřeby předpony oboru názvů ovládacího prvku. V některých případech Pokud pracujete s jinými systémy pro XML, jako je například XSLT nebo XAML, budete muset řízení předpon názvového prostoru. Například pokud výraz XPath, který používá předpony oboru názvů a je součástí šablonu stylů XSLT, musí zajistíte, že váš dokument XML je serializovat s příznakem předpony oboru názvů, které odpovídá používaným ve výrazu XPath.  
  
### <a name="xnamespace-class"></a>Třída XNamespace  
 <xref:System.Xml.Linq.XNamespace> představuje obor názvů pro <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute>. Obory názvů jsou součástí <xref:System.Xml.Linq.XName>.  
  
### <a name="xnode-class"></a>Třída XNode  
 <xref:System.Xml.Linq.XNode> je abstraktní třída představující uzly stromu XML. Následující třídy odvozovat <xref:System.Xml.Linq.XNode> třídy:  
  
-   <xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>Třída XNodeDocumentOrderComparer  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer> poskytuje funkce pro porovnání uzly, aby se jejich pořadí dokumentů.  
  
### <a name="xnodeequalitycomparer-class"></a>Třída XNodeEqualityComparer  
 <xref:System.Xml.Linq.XNodeEqualityComparer> poskytuje funkce pro porovnání uzly pro hodnotu rovnosti.  
  
### <a name="xobject-class"></a>Třída XObject  
 <xref:System.Xml.Linq.XObject> je abstraktní základní třídu z <xref:System.Xml.Linq.XNode> a <xref:System.Xml.Linq.XAttribute>. Poskytuje funkce poznámek a události.  
  
### <a name="xobjectchange-class"></a>Třída XObjectChange  
 <xref:System.Xml.Linq.XObjectChange> Určuje typ události, když událost se vyvolá pro <xref:System.Xml.Linq.XObject>.  
  
### <a name="xobjectchangeeventargs-class"></a>XObjectChangeEventArgs Class  
 <xref:System.Xml.Linq.XObjectChangeEventArgs> poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed> události.  
  
### <a name="xprocessinginstruction-class"></a>Třída XProcessingInstruction  
 <xref:System.Xml.Linq.XProcessingInstruction> představuje instrukce zpracování XML. Instrukce pro zpracování komunikuje informace k aplikaci, která zpracovává XML.  
  
### <a name="xtext-class"></a>Třída XText  
 <xref:System.Xml.Linq.XText> reprezentuje textový uzel. Ve většině případů není nutné použít tuto třídu. Tato třída se používá především pro smíšený obsah.  
  
## <a name="see-also"></a>Viz také:
- [Přehled LINQ to XML programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

---
title: "Literál XML CDATA (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 906fd2494dd952c08088b9b7e38dba4505780481
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-cdata-literal-visual-basic"></a>Literál XML CDATA (Visual Basic)
Literál představující <xref:System.Xml.Linq.XCData> objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Součásti  
 `<![CDATA[`  
 Požadováno. Označuje začátek části XML CDATA.  
  
 `content`  
 Požadováno. Obsah textu se objeví v části XML CDATA.  
  
 `]]>`  
 Požadováno. Označuje konec oddílu.  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XCData> Objektu.  
  
## <a name="remarks"></a>Poznámky  
 XML CDATA částech nezpracovaný text, který by měl být zahrnuty, ale nebyly analyzovány s XML, který jej obsahuje. XML CDATA oddílu může obsahovat jakýkoli text. To zahrnuje vyhrazené znaky jazyka XML. Části XML CDATA končí sekvenci "]] >". To znamená následující body:  
  
-   Výraz vložené v literál XML CDATA nelze použít, protože oddělovače embedded výraz platný obsah XML CDATA.  
  
-   XML CDATA oddíly nelze vnořit, protože `content` nemůže obsahovat hodnotu "]] >".  
  
 Můžete přiřadit literál XML CDATA proměnné nebo její zahrnutí do literál XML elementu.  
  
> [!NOTE]
>  Literál XML může mít rozsah více řádků, ale nepoužívá znaky pokračování řádku. To umožňuje kopírovat obsah z dokumentu XML a vložte ji přímo do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru převede literál XML CDATA volání <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktor.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří oddílu CDATA, který obsahuje text "může obsahovat literálu \<XML > značky".  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XCData>  
 [Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML – literály](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)

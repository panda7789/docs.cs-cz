---
title: "Literál komentáře XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36be34ac22cfe926a2eea946f5e4c4eb534de696
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-literal-visual-basic"></a>Literál komentáře XML (Visual Basic)
Literál představující <xref:System.Xml.Linq.XComment> objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`<!--`|Požadováno. Označuje začátek komentáře XML.|  
|`content`|Požadováno. Text, který se zobrazí v komentáře XML. Nemůže obsahovat dvě pomlčky (-) nebo končit pomlčkou přiléhající k uzavírací značku.|  
|`-->`|Požadováno. Označuje konec komentáře XML.|  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XComment> Objektu.  
  
## <a name="remarks"></a>Poznámky  
 XML – literály komentář neobsahují obsah dokumentu; obsahují informace o dokumentu. V části komentáře XML končí pořadí "-->". To znamená následující body:  
  
-   Výraz vložené v literál komentáře jazyka XML nelze použít, protože oddělovače embedded výraz platný obsah komentáře XML.  
  
-   Komentář oddílech XML nemůže být vnořena, protože `content` nemůže obsahovat hodnotu "-->".  
  
 Literál komentáře jazyka XML je možné přiřadit do proměnné, nebo můžete zahrnout do literál XML elementu.  
  
> [!NOTE]
>  Literál XML může zahrnovat více řádků bez použití znaky pokračování řádku. Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložte ji přímo do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru převede literál XML komentář k volání <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktor.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří komentáře jazyka XML, který obsahuje text "Toto je komentář".  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XComment>  
 [Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML – literály](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)

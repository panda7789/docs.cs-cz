---
title: Literál komentáře XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 93c1346e54106b93f3932a494dea85d082ec994d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400212"
---
# <a name="xml-comment-literal-visual-basic"></a>Literál komentáře XML (Visual Basic)
Literál představující <xref:System.Xml.Linq.XComment> objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`<!--`|Povinná hodnota. Označuje začátek komentáře XML.|  
|`content`|Povinná hodnota. Text, který se má zobrazit v komentáři XML Nemůže obsahovat řadu dvou spojovníků (--) nebo končit spojovníkem, které je vedle uzavírací značky.|  
|`-->`|Povinná hodnota. Označuje konec komentáře XML.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt <xref:System.Xml.Linq.XComment>.  
  
## <a name="remarks"></a>Poznámky  
 Literály komentářů XML neobsahují obsah dokumentu. obsahují informace o dokumentu. Oddíl komentáře XML končí sekvencí "-->". To zahrnuje následující body:  
  
- V literálu komentáře XML nemůžete použít vložený výraz, protože oddělovače vložených výrazů jsou platným obsahem komentáře XML.  
  
- Oddíly komentářů XML nemůžou být vnořené, protože `content` nesmí obsahovat hodnotu-->.  
  
 Můžete přiřadit literál komentáře XML proměnné nebo ji můžete zahrnout do literálu elementu XML.  
  
> [!NOTE]
> Literál XML může zahrnovat více řádků bez použití znaků pro pokračování řádku. Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.  
  
 Kompilátor Visual Basic převádí literál komentáře XML na volání <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktoru.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří komentář XML, který obsahuje text "Toto je komentář".  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XComment>
- [Literál XML elementu](xml-element-literal.md)
- [Literály XML](index.md)
- [Vytvoření XML v jazyce Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)

---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4bcfe96361de9e196cb684ac4ba734f82442e25c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940891"
---
# <a name="param-visual-basic"></a>\<Param > (Visual Basic)
Definuje parametr název a popis.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 Název parametru metody. Název uzavřete do dvojitých uvozovek ("").  
  
 `description`  
 Popis pro parametr.  
  
## <a name="remarks"></a>Poznámky  
 `<param>` Značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu.  
  
 Text `<param>` značky se objeví v následujících umístěních:  
  
- Informace o parametru technologie IntelliSense. Další informace najdete v tématu [pomocí technologie IntelliSense](/visualstudio/ide/using-intellisense).  
  
- Prohlížeč objektů. Další informace najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `<param>` značka, které popisují `id` parametru.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)

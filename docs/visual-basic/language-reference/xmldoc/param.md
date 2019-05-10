---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 91489ee1664da22cc8897cdf8d12b61d962d1c83
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664188"
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

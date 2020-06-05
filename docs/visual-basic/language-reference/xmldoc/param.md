---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: d325d5f9fbfd132630cf280653be214a267a7a80
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400057"
---
# <a name="param-visual-basic"></a>\<param> (Visual Basic)
Definuje název a popis parametru.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 Název parametru metody. Název uzavřete do uvozovek ("").  
  
 `description`  
 Popis parametru  
  
## <a name="remarks"></a>Poznámky  
 `<param>`Značka by měla být použita v komentáři pro deklaraci metody pro popis jednoho z parametrů pro metodu.  
  
 Text `<param>` značky se zobrazí v následujících umístěních:  
  
- Informace o parametrech technologie IntelliSense Další informace najdete v tématu [použití technologie IntelliSense](/visualstudio/ide/using-intellisense).  
  
- Prohlížeč objektů. Další informace naleznete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<param>` značku k popisu `id` parametru.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také

- [Značky pro komentáře XML](index.md)

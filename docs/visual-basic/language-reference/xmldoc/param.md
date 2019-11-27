---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4405fdf2defbb27aa2146d20083fd406d1f07236
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352288"
---
# <a name="param-visual-basic"></a>\<param > (Visual Basic)
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
 Značka `<param>` by měla být použita v komentáři pro deklaraci metody pro popis jednoho z parametrů pro metodu.  
  
 Text značky `<param>` se zobrazí v následujících umístěních:  
  
- Informace o parametrech technologie IntelliSense Další informace najdete v tématu [použití technologie IntelliSense](/visualstudio/ide/using-intellisense).  
  
- Prohlížeč objektů. Další informace naleznete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá značka `<param>` k popisu `id` parametru.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)

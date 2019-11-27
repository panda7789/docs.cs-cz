---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 1cbac2162bd39cdc8af9a55dfd6e2f90bc40b08a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354326"
---
# <a name="code-visual-basic"></a>> kódu \<(Visual Basic)
Označuje, že je text více řádky kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a>Parametry  
 `content`  
 Text, který se má označit jako kód  
  
## <a name="remarks"></a>Poznámky  
 Použijte značku `<code>` k označení více řádků jako kódu. Použijte [\<> c](../../../visual-basic/language-reference/xmldoc/c.md) k označení toho, že text v rámci popisu by měl být označený jako kód.  
  
 Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá značka \<Code > k zahrnutí ukázkového kódu pro použití pole `ID`.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)

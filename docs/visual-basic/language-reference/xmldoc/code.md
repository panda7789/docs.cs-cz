---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: aa65fed863718f1f00b510f82051a13e764e1b23
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400138"
---
# <a name="code-visual-basic"></a>\<code> (Visual Basic)
Označuje, že je text více řádky kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a>Parametry  
 `content`  
 Text, který se má označit jako kód  
  
## <a name="remarks"></a>Poznámky  
 Použijte `<code>` značku k označení více řádků jako kódu. Slouží [\<c>](c.md) k označení, že text v rámci popisu by měl být označen jako kód.  
  
 Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá \<code> značku k zahrnutí příkladu kódu pro použití `ID` pole.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Značky pro komentáře XML](index.md)

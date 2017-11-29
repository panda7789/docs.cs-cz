---
title: "&lt;c&gt; (programování průvodce v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 21c7830c03b0b93e3597835954ac9e7d2feb49e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcgt-c-programming-guide"></a>&lt;c&gt; (programování průvodce v C#)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>Parametry  
 `text`  
 Text, který chcete označit jako kód.  
  
## <a name="remarks"></a>Poznámky  
 \<c > Značka poskytuje způsob, jak znamenat, že text v rámci popis by měl být označen jako kód. Použití [ \<kód >](../../../csharp/programming-guide/xmldoc/code.md) k označení jako kódu více řádků.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Doporučené značky pro dokumentační komentáře](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

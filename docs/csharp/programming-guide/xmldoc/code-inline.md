---
title: Průvodce C# programováním <c>
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: 97d5949a1a1528befeffdc27a3e727ac510e8da2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75697231"
---
# <a name="c-c-programming-guide"></a>\<> c (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>Parametry  
 `text`  
 Text, který chcete označit jako kód.  
  
## <a name="remarks"></a>Poznámky  
 Značka \<c > poskytuje způsob, jak označit, že text v rámci popisu by měl být označen jako kód. Použijte [\<> kódu](./code.md) k označení více řádků jako kódu.  
  
 Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

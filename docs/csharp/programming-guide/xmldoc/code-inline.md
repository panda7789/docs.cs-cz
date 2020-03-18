---
title: <c>- Průvodce programováním jazyka C#
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
ms.openlocfilehash: d5b28ee6db52d191f8454592d792ac0a1e1dc73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793458"
---
# <a name="c-c-programming-guide"></a>\<c> (průvodce programováním jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<c>text</c>
```

## <a name="parameters"></a>Parametry

- `text`

  Text, který chcete označit jako kód.

## <a name="remarks"></a>Poznámky

Značka \<c> umožňuje označit, že text v popisu by měl být označen jako kód. Pomocí [ \<kódu>](./code.md) označit více řádků jako kód.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

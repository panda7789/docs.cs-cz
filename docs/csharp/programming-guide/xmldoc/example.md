---
title: <example> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: 615eccbc427b6a5bbbed061acd0c8b0b9be7f46c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789820"
---
# <a name="example-c-programming-guide"></a>\<příklad> (průvodce programováním jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<example>description</example>
```

## <a name="parameters"></a>Parametry

- `description`

  Popis ukázky kódu.

## <a name="remarks"></a>Poznámky

V \<příkladu> značka umožňuje určit příklad použití metody nebo jiného člena knihovny. To obvykle zahrnuje použití [ \<kódu>](./code.md) značky.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

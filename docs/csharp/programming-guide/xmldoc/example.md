---
title: <example> – Průvodce programováním v C#
description: Další informace o XML <example> Inteligentní. Tato značka umožňuje zadat příklad použití metody nebo jiného člena knihovny.
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: dd529e8f2a54cf9086d0d8c555dd1adb70b99126
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381525"
---
# <a name="example-c-programming-guide"></a>\<example>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<example>description</example>
```

## <a name="parameters"></a>Parametry

- `description`

  Popis ukázky kódu.

## <a name="remarks"></a>Poznámky

`<example>`Značka umožňuje zadat příklad použití metody nebo jiného člena knihovny. To běžně zahrnuje použití [\<code>](./code.md) značky.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

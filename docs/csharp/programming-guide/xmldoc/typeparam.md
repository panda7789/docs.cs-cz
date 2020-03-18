---
title: <typeparam> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793369"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam> (průvodce programováním C#)

## <a name="syntax"></a>Syntaxe

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a>Parametry

- `name`

  Název parametru typu. Název uzavřete do uvozovek (" ").

- `description`

  Popis parametru typu.

## <a name="remarks"></a>Poznámky

Značka `<typeparam>` by měla být použita v komentáři pro obecný typ nebo deklaraci metody k popisu parametru typu. Přidejte značku pro každý parametr typu obecného typu nebo metody.

Další informace naleznete [v tématu Generics](../generics/index.md).

Text značky `<typeparam>` se zobrazí v intelliSense, webové zprávě s komentářem kódu [prohlížeče objektů.](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser)

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../../language-reference/index.md)
- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

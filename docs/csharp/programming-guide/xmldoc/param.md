---
title: <param> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789763"
---
# <a name="param-c-programming-guide"></a>\<param> (průvodce programováním C#)

## <a name="syntax"></a>Syntaxe

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>Parametry

- `name`

  Název parametru metody. Název uzavřete do uvozovek (" ").

- `description`

  Popis parametru.

## <a name="remarks"></a>Poznámky

Značka \<param> by měla být použita v komentáři pro deklaraci metody k popisu jednoho z parametrů metody. Chcete-li dokumentovat více \<parametrů, použijte více značek> param.

Text značky \<param> se zobrazí v aplikaci IntelliSense, prohlížeči objektů a ve webové zprávě Skomentářem kódu.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

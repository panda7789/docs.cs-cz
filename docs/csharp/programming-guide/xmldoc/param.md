---
title: <param> – Průvodce programováním v C#
description: Další informace o XML <param> Inteligentní. Tato značka se používá v komentáři pro deklaraci metody k popisu jednoho z parametrů pro metodu.
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: a9e3b2e86528afcbe1330788e248f0143efb5c1b
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381551"
---
# <a name="param-c-programming-guide"></a>\<param>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>Parametry

- `name`

  Název parametru metody. Název uzavřete do uvozovek ("").

- `description`

  Popis parametru

## <a name="remarks"></a>Poznámky

`<param>`Značka by měla být použita v komentáři pro deklaraci metody pro popis jednoho z parametrů pro metodu. Chcete-li dokumentovat více parametrů, použijte více `<param>` značek.

Text `<param>` značky je zobrazen v IntelliSense, prohlížeč objektů a webové sestavy komentáře kódu.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

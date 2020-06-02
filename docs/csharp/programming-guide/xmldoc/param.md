---
title: <param> – Průvodce programováním v C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 396ed716c246091a674268020261069f36dd2be8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287321"
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

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

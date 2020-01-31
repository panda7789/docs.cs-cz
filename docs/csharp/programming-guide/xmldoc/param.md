---
title: <param> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789763"
---
# <a name="param-c-programming-guide"></a>> param \<C# (Průvodce programováním)

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

Značka > param \<by měla být použita v komentáři pro deklaraci metody pro popis jednoho z parametrů pro metodu. Chcete-li dokumentovat více parametrů, použijte více značek > param \<.

Text značky > param \<se zobrazí v IntelliSense, v Prohlížeč objektů a v webové sestavě komentáře kódu.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Viz také:

- [C#Průvodce programováním](../index.md)
- [Doporučené značky pro dokumentační komentáře](./recommended-tags-for-documentation-comments.md)

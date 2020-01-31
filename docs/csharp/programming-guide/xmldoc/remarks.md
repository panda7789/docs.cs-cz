---
title: <remarks> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793376"
---
# <a name="remarks-c-programming-guide"></a>\<poznámky > (C# Průvodce programováním)

## <a name="syntax"></a>Syntaxe

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parametry

- `Description`

  Popis člena

## <a name="remarks"></a>Poznámky

Značka \<poznámky > se používá k přidání informací o typu, doplňování informací zadaných s [\<souhrn >](./summary.md). Tyto informace se zobrazí v okně Prohlížeč objektů.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro dokumentační komentáře](./recommended-tags-for-documentation-comments.md)

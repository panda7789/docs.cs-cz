---
title: <remarks> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793376"
---
# <a name="remarks-c-programming-guide"></a>\<poznámky> (průvodce programováním jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parametry

- `Description`

  Popis člena.

## <a name="remarks"></a>Poznámky

Poznámka \<> značka se používá k přidání informací o typu, doplnění informací určených [ \<souhrnem>](./summary.md). Tyto informace se zobrazí v okně Prohlížeč objektů.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

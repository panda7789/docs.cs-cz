---
title: <remarks> – Průvodce programováním v C#
description: Další informace o XML <remarks> Inteligentní. Tato značka slouží k přidání informací o typu, doplňování informací zadaných s <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: d38905d100e24158e7a1412f6be9f01a7ced2382
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381499"
---
# <a name="remarks-c-programming-guide"></a>\<remarks>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parametry

- `Description`

  Popis člena

## <a name="remarks"></a>Poznámky

`<remarks>`Značka slouží k přidání informací o typu a doplňování informací zadaných s [\<summary>](./summary.md) . Tyto informace se zobrazí v okně Prohlížeč objektů.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

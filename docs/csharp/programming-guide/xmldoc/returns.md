---
title: <returns> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 784d9effa589c962b8a2b982fd199f74309fb4dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789712"
---
# <a name="returns-c-programming-guide"></a>\<vrátí> (průvodce programováním jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<returns>description</returns>
```

## <a name="parameters"></a>Parametry

- `description`

  Popis vrácené hodnoty.

## <a name="remarks"></a>Poznámky

Vratná \<značka> by měla být použita v komentáři pro deklaraci metody k popisu vrácené hodnoty.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

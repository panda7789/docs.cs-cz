---
title: <returns> – Průvodce programováním v C#
description: Další informace o XML <returns> Inteligentní. Tato značka se používá v komentáři pro deklaraci metody k popisu návratové hodnoty.
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: e461d46df619a351048ae7942e59847d39e490f9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381395"
---
# <a name="returns-c-programming-guide"></a>\<returns>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<returns>description</returns>
```

## <a name="parameters"></a>Parametry

- `description`

  Popis návratové hodnoty.

## <a name="remarks"></a>Poznámky

`<returns>`Značka by měla být použita v komentáři pro deklaraci metody k popisu návratové hodnoty.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

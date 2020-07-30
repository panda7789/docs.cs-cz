---
title: <para> – Průvodce programováním v C#
description: Další informace o XML <para> Inteligentní. Tato značka umožňuje přidat strukturu na text v jiné značce, například <summary>, <remarks>, nebo <returns>.
ms.date: 07/20/2015
f1_keywords:
- <para>
- para
helpviewer_keywords:
- <para> C# XML tag
- para C# XML tag
ms.assetid: c74b8705-29df-40b1-bff5-237492b0e978
ms.openlocfilehash: 146078bcb556b4085724ddcdac561ea868ab0481
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381850"
---
# <a name="para-c-programming-guide"></a>\<para>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<para>content</para>
```

## <a name="parameters"></a>Parametry

- `content`

  Text odstavce

## <a name="remarks"></a>Poznámky

`<para>`Značka je určena pro použití uvnitř značky, jako například [\<summary>](./summary.md) , [\<remarks>](./remarks.md) nebo [\<returns>](./returns.md) , a umožňuje přidat do textu strukturu.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

Příklad použití naleznete v tématu [\<summary>](./summary.md) `<para>` .

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

---
title: <seealso> – Průvodce programováním v C#
description: Naučte se používat XML. <seealso> Inteligentní. Tato značka vám umožní určit text, který se může zobrazit v části Viz také.
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e8618ef352a4fa7f0fd4c88733c6568b0e12e376
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380641"
---
# <a name="seealso-c-programming-guide"></a>\<seealso>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>Parametry

- cref = " `member`"

  Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.`member` v uvozovkách ("") se musí vyskytovat.

  Informace o tom, jak vytvořit odkaz cref na obecný typ, naleznete v tématu [atribut cref](./cref-attribute.md).

## <a name="remarks"></a>Poznámky

`<seealso>`Značka vám umožní určit text, který se může objevit v části Viz také. Slouží [\<see>](./see.md) k zadání odkazu z textu.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

Příklad použití naleznete v tématu [\<summary>](./summary.md) \<seealso> .

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

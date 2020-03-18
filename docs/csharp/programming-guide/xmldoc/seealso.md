---
title: <seealso> - Průvodce programováním jazyka C#
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
ms.openlocfilehash: e24d5910ab21f01aebb5a32ce7646cf56886a81a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093458"
---
# <a name="seealso-c-programming-guide"></a>\<seealso> (Průvodce programováním Jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>Parametry

- cref = " `member`"

  Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.`member` musí být uvedeny v uvozovkách (" ").

  Informace o tom, jak vytvořit odkaz na obecný typ, naleznete v [atributu cref](./cref-attribute.md).

## <a name="remarks"></a>Poznámky

Značka \<seealso> umožňuje určit text, který se může chtít zobrazit v části Viz také. Pomocí [ \<>můžete](./see.md) zadat odkaz z textu.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

## <a name="example"></a>Příklad

Viz [ \<souhrnné>](./summary.md) příklad \<použití viz také>.

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

---
title: <seealso> – C# Průvodce programováním
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
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093458"
---
# <a name="seealso-c-programming-guide"></a>\<SeeAlso > (C# Průvodce programováním)

## <a name="syntax"></a>Syntaxe

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>Parametry

- cref = " `member`"

  Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.`member` v uvozovkách ("") se musí vyskytovat.

  Informace o tom, jak vytvořit odkaz cref na obecný typ, naleznete v tématu [atribut cref](./cref-attribute.md).

## <a name="remarks"></a>Poznámky

Značka > \<SeeAlso umožňuje určit text, který se může objevit v části Viz také. Použijte [\<v části >](./see.md) určete odkaz z textu.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

Příklad použití \<SeeAlso > najdete v článku [> souhrnu\<](./summary.md) .

## <a name="see-also"></a>Viz také

- [C#Průvodce programováním](../index.md)
- [Doporučené značky pro dokumentační komentáře](./recommended-tags-for-documentation-comments.md)

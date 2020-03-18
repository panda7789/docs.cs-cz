---
title: <see>- Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: f4834f88c646b44269f8290c2ad08698c34e714a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627669"
---
# <a name="see-c-programming-guide"></a>\<viz> (průvodce programováním jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Parametry

- cref =`member`" "

  Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML. Umístěte *člen* do uvozovek (" ").

## <a name="remarks"></a>Poznámky

Značka \<viz> umožňuje zadat odkaz z textu. Použijte [ \<také>see](./seealso.md) označuje, že text by měl být umístěn v části Viz také. Pomocí [atributu cref](./cref-attribute.md) vytvořte interní hypertextové odkazy na stránky dokumentace pro prvky kódu.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

Následující příklad ukazuje \<značku> v souhrnné části.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

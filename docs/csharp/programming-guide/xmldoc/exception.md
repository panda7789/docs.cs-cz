---
title: <exception>- Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 14318ac0b0cdf781d0488eecaf934879017d91f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789807"
---
# <a name="exception-c-programming-guide"></a>\<výjimka> (průvodce programováním Jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a>Parametry

- cref = " `member`"

  Odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace. Kompilátor zkontroluje, zda daná `member` výjimka existuje, a překládá se do názvu kanonického prvku ve výstupním XML. `member`musí být uvedeny v uvozovkách (" ").

  Další informace o formátování `member` pro odkaz na obecný typ naleznete [v tématu Zpracování souboru XML](processing-the-xml-file.md).

- `description`

  Popis výjimky.

## <a name="remarks"></a>Poznámky

Značka \<> výjimky umožňuje určit, které výjimky mohou být vyvolány. Tuto značku lze použít pro definice metod, vlastností, událostí a indexerů.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

Další informace o zpracování výjimek naleznete v [tématu Výjimky a zpracování výjimek](../exceptions/index.md).

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](recommended-tags-for-documentation-comments.md)

---
title: Průvodce C# programováním <exception>
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 14318ac0b0cdf781d0488eecaf934879017d91f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789807"
---
# <a name="exception-c-programming-guide"></a>> \<výjimky (C# Průvodce programováním)

## <a name="syntax"></a>Syntaxe

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a>Parametry

- cref = " `member`"

  Odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace. Kompilátor kontroluje, zda daná výjimka existuje, a překládá `member` na název kanonického prvku ve výstupním souboru XML. `member` musí být v uvozovkách ("").

  Další informace o tom, jak formátovat `member` pro odkazování na obecný typ, naleznete v tématu [zpracování souboru XML](processing-the-xml-file.md).

- `description`

  Popis výjimky

## <a name="remarks"></a>Poznámky

Značka > \<výjimky umožňuje určit, které výjimky mohou být vyvolány. Tato značka se dá použít na definice pro metody, vlastnosti, události a indexery.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

Další informace o zpracování výjimek naleznete v tématu [výjimky a zpracování výjimek](../exceptions/index.md).

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a>Viz také:

- [C#Průvodce programováním](../index.md)
- [Doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments.md)

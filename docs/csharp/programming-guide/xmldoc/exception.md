---
title: <exception>– Průvodce programováním v C#
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: fb193c586456497ee60aad941d56241ad7c6b63a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287379"
---
# <a name="exception-c-programming-guide"></a>\<exception>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a>Parametry

- cref = " `member`"

  Odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace. Kompilátor kontroluje, zda daná výjimka existuje, a překládá se na `member` kanonický název elementu ve výstupním souboru XML. `member`v uvozovkách ("") se musí vyskytovat.

  Další informace o tom, jak formátovat `member` pro odkazování na obecný typ, naleznete v tématu [zpracování souboru XML](processing-the-xml-file.md).

- `description`

  Popis výjimky

## <a name="remarks"></a>Poznámky

`<exception>`Značka umožňuje určit, které výjimky mohou být vyvolány. Tato značka se dá použít na definice pro metody, vlastnosti, události a indexery.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

Další informace o zpracování výjimek naleznete v tématu [výjimky a zpracování výjimek](../exceptions/index.md).

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](recommended-tags-for-documentation-comments.md)

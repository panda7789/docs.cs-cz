---
title: <exception>– Průvodce programováním v C#
description: Přečtěte si o <exception> značce XML. Tato značka vám umožní určit, které výjimky mohou být vyvolány a lze je použít na metody, vlastnosti, události a indexery.
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 22a28f3fe6de5a0db9aea0f1fd7963d4e6fcee05
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381733"
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

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](recommended-tags-for-documentation-comments.md)

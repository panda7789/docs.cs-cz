---
title: <typeparam> – Průvodce programováním v C#
description: Další informace o XML <typeparam> Inteligentní. Tato značka se používá v komentáři pro obecný typ nebo deklaraci metody pro popis parametru typu.
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 5e5333e384e8c77b500f74ab7c6038146df6e2c0
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380784"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a>Parametry

- `name`

  Název parametru typu. Název uzavřete do uvozovek ("").

- `description`

  Popis parametru typu.

## <a name="remarks"></a>Poznámky

`<typeparam>`Značka by měla být použita v komentáři pro obecný typ nebo deklaraci metody pro popis parametru typu. Přidejte značku pro každý parametr typu obecného typu nebo metody.

Další informace najdete v tématu [Obecné typy](../generics/index.md).

Text `<typeparam>` značky bude zobrazen v IntelliSense, Webová sestava komentáře kódu [prohlížeč objektůho okna](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) .

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace k jazyku C#](../../language-reference/index.md)
- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

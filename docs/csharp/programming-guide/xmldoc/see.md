---
title: <see>– Průvodce programováním v C#
description: Přečtěte si o <see> značce XML. Tato značka umožňuje zadat odkaz v rámci textu, například pomocí atributu cref.
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
ms.openlocfilehash: 1cc4982d1ebe9d6896404218a6d200b10cc6503f
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381928"
---
# <a name="see-c-programming-guide"></a>\<see>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Parametry

- cref = " `member` "

  Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML. Umístit *člena* v uvozovkách ("").

## <a name="remarks"></a>Poznámky

`<see>`Značka umožňuje zadat odkaz v rámci textu. Použijte [\<seealso>](./seealso.md) k označení, že text by měl být umístěn v části Viz také. Pomocí [atributu cref](./cref-attribute.md) můžete vytvořit interní hypertextové odkazy na stránky dokumentace pro prvky kódu. Také ``href`` je platný atribut, který bude fungovat jako hypertextový odkaz.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

Následující příklad ukazuje `<see>` značku v rámci oddílu Summary.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

---
title: <value> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793353"
---
# <a name="value-c-programming-guide"></a>\<> hodnoty (průvodce programováním Jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parametry

- `property-description`

  Popis vlastnosti.

## <a name="remarks"></a>Poznámky

Značka \<> hodnoty umožňuje popsat hodnotu, kterou představuje vlastnost. Všimněte si, že když přidáte vlastnost pomocí průvodce kódem ve vývojovém prostředí Sady Visual Studio .NET, přidá [ \<souhrnnou značku>](./summary.md) pro novou vlastnost. Potom byste měli ručně \<přidat hodnotu> značku k popisu hodnoty, která představuje vlastnost.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

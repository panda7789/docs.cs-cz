---
title: <value> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793353"
---
# <a name="value-c-programming-guide"></a>> hodnota \<(C# Průvodce programováním)

## <a name="syntax"></a>Syntaxe

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parametry

- `property-description`

  Popis vlastnosti

## <a name="remarks"></a>Poznámky

Hodnota \<> tag umožňuje popsat hodnotu, kterou vlastnost představuje. Všimněte si, že při přidání vlastnosti přes průvodce kódem ve vývojovém prostředí sady Visual Studio .NET bude přidána značka [\<summary >](./summary.md) pro novou vlastnost. Měli byste pak ručně přidat \<Value > tag k popisu hodnoty, kterou vlastnost představuje.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Viz také:

- [C#Průvodce programováním](../index.md)
- [Doporučené značky pro dokumentační komentáře](./recommended-tags-for-documentation-comments.md)

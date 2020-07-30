---
title: <value> – Průvodce programováním v C#
description: Další informace o XML <value> Inteligentní. Tato značka umožňuje popsat hodnotu, kterou vlastnost představuje.
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: d8294b477d7067653c71d1ec2047a85a0bfe6d02
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380771"
---
# <a name="value-c-programming-guide"></a>\<value>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parametry

- `property-description`

  Popis vlastnosti

## <a name="remarks"></a>Poznámky

`<value>`Značka umožňuje popsat hodnotu, kterou vlastnost představuje. Když přidáte vlastnost prostřednictvím průvodce kódem ve vývojovém prostředí sady Visual Studio .NET, přidá se [\<summary>](./summary.md) značka pro novou vlastnost. Měli byste pak ručně přidat `<value>` značku pro popis hodnoty, kterou vlastnost představuje.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

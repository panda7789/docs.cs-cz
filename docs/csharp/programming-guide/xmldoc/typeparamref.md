---
title: <typeparamref>– Průvodce programováním v C#
description: Přečtěte si o <typeparamref> značce XML. Tato značka umožňuje uživatelům souboru dokumentace naformátovat nějaký text nějakým způsobem, například kurzívou.
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: a39e896f1242452c7bcc94faa1e7ef3086ae2149
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380719"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>Parametry

- `name`

  Název parametru typu. Název uzavřete do uvozovek ("").

## <a name="remarks"></a>Poznámky

Další informace o parametrech typu v obecných typech a metodách naleznete v tématu [generické](../generics/index.md)typy.

Pomocí této značky můžete uživatelům souboru dokumentace povolit formátování určitého slova nějakým způsobem, například kurzívou.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

---
title: <typeparamref>- Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789662"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref> (průvodce programováním jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>Parametry

- `name`

  Název parametru typu. Název uzavřete do uvozovek (" ").

## <a name="remarks"></a>Poznámky

Další informace o parametrech typu v obecných typech a metodách naleznete v [tématu Generics](../generics/index.md).

Pomocí této značky můžete spotřebitelům souboru dokumentace umožnit formátovat slovo nějakým odlišným způsobem, například kurzívou.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

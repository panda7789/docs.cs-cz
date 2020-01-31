---
title: Průvodce C# programováním <typeparamref>
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789662"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref > (C# Průvodce programováním)

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

- [C#Průvodce programováním](../index.md)
- [Doporučené značky pro dokumentační komentáře](./recommended-tags-for-documentation-comments.md)

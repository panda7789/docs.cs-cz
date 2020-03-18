---
title: <permission> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 4f76d28d5531c1b9f01fa950589407934cc1244a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093471"
---
# <a name="permission-c-programming-guide"></a>\<> oprávnění (průvodce programováním jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Parametry

- cref = " `member`"

  Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor zkontroluje, zda daný prvek `member` kódu existuje, a překládá se do názvu kanonického prvku ve výstupním XML. *člen* musí být uveden v uvozovkách (" ").

  Informace o tom, jak vytvořit odkaz na obecný typ, naleznete v [atributu cref](./cref-attribute.md).

- `description`

  Popis přístupu k členu.

## <a name="remarks"></a>Poznámky

Značka \<oprávnění> umožňuje dokumentovat přístup člena. Třída <xref:System.Security.PermissionSet> umožňuje určit přístup k členu.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

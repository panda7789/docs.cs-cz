---
title: <permission> – Průvodce programováním v C#
description: Další informace o XML <permission> Inteligentní. Tato značka vám umožní zdokumentovat přístup člena, zatímco třída PermissionSet vám umožní určit přístup ke členu.
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 38c87505b8b2973875e474ffd296dc02b7fb9de6
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381720"
---
# <a name="permission-c-programming-guide"></a>\<permission>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Parametry

- cref = " `member`"

  Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje, a překládá se na `member` název kanonického prvku ve výstupním souboru XML. *člen* musí být v uvozovkách ("").

  Informace o tom, jak vytvořit odkaz cref na obecný typ, naleznete v tématu [atribut cref](./cref-attribute.md).

- `description`

  Popis přístupu ke členovi.

## <a name="remarks"></a>Poznámky

`<permission>`Značka vám umožní dokumentovat přístup člena. <xref:System.Security.PermissionSet>Třída umožňuje zadat přístup ke členu.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

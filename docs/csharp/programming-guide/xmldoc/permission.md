---
title: <permission> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 4f76d28d5531c1b9f01fa950589407934cc1244a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093471"
---
# <a name="permission-c-programming-guide"></a>> oprávnění \<(C# Průvodce programováním)

## <a name="syntax"></a>Syntaxe

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Parametry

- cref = " `member`"

  Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje, a překládá `member` na název kanonického prvku ve výstupním souboru XML. *člen* musí být v uvozovkách ("").

  Informace o tom, jak vytvořit odkaz cref na obecný typ, naleznete v tématu [atribut cref](./cref-attribute.md).

- `description`

  Popis přístupu ke členovi.

## <a name="remarks"></a>Poznámky

> Značka \<oprávnění umožňuje dokumentovat přístup člena. Třída <xref:System.Security.PermissionSet> umožňuje zadat přístup ke členu.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Viz také

- [C#Průvodce programováním](../index.md)
- [Doporučené značky pro dokumentační komentáře](./recommended-tags-for-documentation-comments.md)

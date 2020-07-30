---
title: <list> – Průvodce programováním v C#
description: Další informace o XML <list> Inteligentní. Tato značka slouží k vytváření tabulek a definic, odrážek nebo číslovaných seznamů pomocí bloků Item.
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 361c2e6f343554a9b8519c3b2e41219b209e682d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381863"
---
# <a name="list-c-programming-guide"></a>\<list>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<list type="bullet|number|table">
    <listheader>
        <term>term</term>
        <description>description</description>
    </listheader>
    <item>
        <term>term</term>
        <description>description</description>
    </item>
</list>
```

## <a name="parameters"></a>Parametry

- `term`

  Pojem, který definuje, který bude definován v `description` .

- `description`

  Buď položka v seznamu odrážek nebo číslovaný seznam, nebo definice `term` .
  
## <a name="remarks"></a>Poznámky

Tento `<listheader>` blok slouží k definování řádku záhlaví seznamu tabulek nebo definic. Při definování tabulky stačí zadat položku pro termín v záhlaví.

Každá položka v seznamu je určena `<item>` blokem. Při vytváření seznamu definic budete muset zadat i `term` `description` . U tabulky, seznamu s odrážkami nebo číslovaného seznamu ale stačí zadat položku pro `description` .

Seznam nebo tabulka může mít tolik `<item>` bloků, kolik potřebujete.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

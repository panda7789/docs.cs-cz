---
title: <list> - Průvodce programováním jazyka C#
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
ms.openlocfilehash: cb289b26e9bc12d561892c421fb40da18d8c3513
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789743"
---
# <a name="list-c-programming-guide"></a>\<seznam> (Průvodce programováním jazyka C#)

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

  Termín definovat, který bude definován `description`v .

- `description`

  Položka v odrážkách nebo číslovaném seznamu `term`nebo definice .
  
## <a name="remarks"></a>Poznámky

Blok \<> záhlaví seznamu se používá k definování řádku záhlaví tabulky nebo seznamu definic. Při definování tabulky stačí zadat položku termínu v nadpisu.

Každá položka v seznamu je \<určena položkou> bloku. Při vytváření seznamu definic bude nutné `term` zadat `description`obě a . Pro tabulku, seznam s odrážkami nebo číslovaný seznam však `description`stačí zadat položku pro .

Seznam nebo tabulka může \<mít libovolný počet položek> bloky podle potřeby.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

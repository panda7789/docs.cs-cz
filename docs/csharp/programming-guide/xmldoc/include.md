---
title: <include> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 22d87559766c04e53141e843ee8768c8aab89a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156971"
---
# <a name="include-c-programming-guide"></a>\<zahrnout> (Průvodce programováním jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a>Parametry

- `filename`

  Název souboru XML obsahujícího dokumentaci. Název souboru může být kvalifikován s cestou vzhledem k souboru zdrojového kódu. Uzavřete `filename` do jednoduchých uvozovek (' ').

- `tagpath`

  Cesta značek, `filename` které vedou ke `name`značce . Cestu uzavřete do jednoduchých uvozovek (" ').

- `name`

  Specifikátor názvu ve značce, která předchází komentáře; `name` bude mít `id`.

- `id`

ID značky, která předchází komentáře. ID uzavřete do uvozovek (" ").

## <a name="remarks"></a>Poznámky

Značka \<include> umožňuje odkazovat na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu. Toto je alternativa k umístění komentáře dokumentace přímo do souboru zdrojového kódu. Vložením dokumentace do samostatného souboru můžete použít správou zdrojového kódu pro dokumentaci odděleně od zdrojového kódu. Jedna osoba může mít soubor zdrojového kódu rezervován a někdo jiný může mít soubor dokumentace rezervován.

Značka \<include> používá syntaxi xml xpath. Způsoby přizpůsobení> použití aplikace \<XPath naleznete v dokumentaci ke silnici XPath.

## <a name="example"></a>Příklad

Toto je příklad více souborů. Následuje první soubor, který \<používá include>.

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

Druhý *soubor, xml_include_tag.doc*, obsahuje následující komentáře dokumentace.

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a>Výstup programu

Následující výstup se generuje při kompilaci tříd Test a Test2 `-doc:DocFileName.xml.` s následujícím příkazovým řádkem: V sadě Visual Studio zadáte možnost komentáře dokumentu XML v podokně sestavení Návrháře projektu. Když kompilátor Jazyka C# vidí značku \<include>, bude hledat komentáře dokumentace v xml_include_tag.doc namísto aktuálního zdrojového souboru. Kompilátor pak generuje DocFileName.xml, a to je soubor, který je spotřebován nástroje dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) k vytvoření konečné dokumentace.  
  
```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xml_include_tag</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Doporučené značky pro komentáře k dokumentaci](./recommended-tags-for-documentation-comments.md)

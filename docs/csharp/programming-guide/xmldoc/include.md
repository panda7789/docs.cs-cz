---
title: <include> – Průvodce programováním v C#
description: Další informace o XML <include> Inteligentní. Tato značka vám umožní odkazovat na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu.
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 15a99444d464594cc91a7c8805c564c703c3b608
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381902"
---
# <a name="include-c-programming-guide"></a>\<include>(Průvodce programováním v C#)

## <a name="syntax"></a>Syntaxe

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a>Parametry

- `filename`

  Název souboru XML, který obsahuje dokumentaci. Název souboru může být kvalifikován cestou relativní k souboru zdrojového kódu. Uzavřete `filename` do jednoduchých uvozovek (' ').

- `tagpath`

  Cesta značek v `filename` , která vede k označení `name` . Uzavřete cestu do jednoduchých uvozovek (' ').

- `name`

  Specifikátor názvu ve značce, který předchází komentářům; `name`bude mít `id` .

- `id`

ID značky, která předchází komentář. ID uzavřete do dvojitých uvozovek ("").

## <a name="remarks"></a>Poznámky

`<include>`Značka vám umožní odkazovat na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu. Toto je alternativa k umístění dokumentačních komentářů přímo do souboru zdrojového kódu. Vložením dokumentace do samostatného souboru můžete použít správu zdrojového kódu v dokumentaci samostatně ze zdrojového kódu. Je možné, že soubor zdrojového kódu je zarezervován a někdo jiný může mít zarezervován soubor dokumentace.

`<include>`Značka používá syntaxi XPath XML. Způsoby přizpůsobení použití naleznete v dokumentaci XPath `<include>` .

## <a name="example"></a>Příklad

Toto je příklad vícesouborového typu. Následuje první soubor, který používá `<include>` .

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

Druhý soubor, *xml_include_tag.doc*, obsahuje následující dokumentační komentáře.

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

Následující výstup je generován při kompilaci třídy test a Test2 pomocí následujícího příkazového řádku: `-doc:DocFileName.xml.` v aplikaci Visual Studio zadáte možnost komentáře k dokumentu XML v podokně sestavení Návrháře projektu. Když kompilátor jazyka C# uvidí `<include>` značku, vyhledá v *xml_include_tag.doc* komentáře k dokumentaci místo aktuálního zdrojového souboru. Kompilátor potom vygeneruje *DocFileName.xml*a jedná se o soubor, který je využíván nástroji dokumentace, jako je [Sandcastle](https://github.com/EWSoftware/SHFB) , k vytvoření konečné dokumentace.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro dokumentační komentáře](./recommended-tags-for-documentation-comments.md)

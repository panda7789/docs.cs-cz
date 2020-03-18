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
# <a name="include-c-programming-guide"></a><span data-ttu-id="1d9d3-102">\<zahrnout> (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1d9d3-102">\<include> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d9d3-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d9d3-103">Syntax</span></span>

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a><span data-ttu-id="1d9d3-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d9d3-104">Parameters</span></span>

- `filename`

  <span data-ttu-id="1d9d3-105">Název souboru XML obsahujícího dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="1d9d3-106">Název souboru může být kvalifikován s cestou vzhledem k souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="1d9d3-107">Uzavřete `filename` do jednoduchých uvozovek (' ').</span><span class="sxs-lookup"><span data-stu-id="1d9d3-107">Enclose `filename` in single quotation marks (' ').</span></span>

- `tagpath`

  <span data-ttu-id="1d9d3-108">Cesta značek, `filename` které vedou ke `name`značce .</span><span class="sxs-lookup"><span data-stu-id="1d9d3-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="1d9d3-109">Cestu uzavřete do jednoduchých uvozovek (" ').</span><span class="sxs-lookup"><span data-stu-id="1d9d3-109">Enclose the path in single quotation marks (' ').</span></span>

- `name`

  <span data-ttu-id="1d9d3-110">Specifikátor názvu ve značce, která předchází komentáře; `name` bude mít `id`.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>

- `id`

<span data-ttu-id="1d9d3-111">ID značky, která předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="1d9d3-112">ID uzavřete do uvozovek (" ").</span><span class="sxs-lookup"><span data-stu-id="1d9d3-112">Enclose the ID in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="1d9d3-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d9d3-113">Remarks</span></span>

<span data-ttu-id="1d9d3-114">Značka \<include> umožňuje odkazovat na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="1d9d3-115">Toto je alternativa k umístění komentáře dokumentace přímo do souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="1d9d3-116">Vložením dokumentace do samostatného souboru můžete použít správou zdrojového kódu pro dokumentaci odděleně od zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="1d9d3-117">Jedna osoba může mít soubor zdrojového kódu rezervován a někdo jiný může mít soubor dokumentace rezervován.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>

<span data-ttu-id="1d9d3-118">Značka \<include> používá syntaxi xml xpath.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="1d9d3-119">Způsoby přizpůsobení> použití aplikace \<XPath naleznete v dokumentaci ke silnici XPath.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>

## <a name="example"></a><span data-ttu-id="1d9d3-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d9d3-120">Example</span></span>

<span data-ttu-id="1d9d3-121">Toto je příklad více souborů.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-121">This is a multifile example.</span></span> <span data-ttu-id="1d9d3-122">Následuje první soubor, který \<používá include>.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-122">The following is the first file, which uses \<include>.</span></span>

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

<span data-ttu-id="1d9d3-123">Druhý *soubor, xml_include_tag.doc*, obsahuje následující komentáře dokumentace.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-123">The second file, *xml_include_tag.doc*, contains the following documentation comments.</span></span>

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

## <a name="program-output"></a><span data-ttu-id="1d9d3-124">Výstup programu</span><span class="sxs-lookup"><span data-stu-id="1d9d3-124">Program output</span></span>

<span data-ttu-id="1d9d3-125">Následující výstup se generuje při kompilaci tříd Test a Test2 `-doc:DocFileName.xml.` s následujícím příkazovým řádkem: V sadě Visual Studio zadáte možnost komentáře dokumentu XML v podokně sestavení Návrháře projektu.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `-doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="1d9d3-126">Když kompilátor Jazyka C# vidí značku \<include>, bude hledat komentáře dokumentace v xml_include_tag.doc namísto aktuálního zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="1d9d3-127">Kompilátor pak generuje DocFileName.xml, a to je soubor, který je spotřebován nástroje dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) k vytvoření konečné dokumentace.</span><span class="sxs-lookup"><span data-stu-id="1d9d3-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d9d3-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d9d3-128">See also</span></span>

- [<span data-ttu-id="1d9d3-129">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1d9d3-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1d9d3-130">Doporučené značky pro komentáře k dokumentaci</span><span class="sxs-lookup"><span data-stu-id="1d9d3-130">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)

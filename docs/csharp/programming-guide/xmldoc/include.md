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
# <a name="include-c-programming-guide"></a><span data-ttu-id="41213-105">\<include>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="41213-105">\<include> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="41213-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41213-106">Syntax</span></span>

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a><span data-ttu-id="41213-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="41213-107">Parameters</span></span>

- `filename`

  <span data-ttu-id="41213-108">Název souboru XML, který obsahuje dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="41213-108">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="41213-109">Název souboru může být kvalifikován cestou relativní k souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="41213-109">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="41213-110">Uzavřete `filename` do jednoduchých uvozovek (' ').</span><span class="sxs-lookup"><span data-stu-id="41213-110">Enclose `filename` in single quotation marks (' ').</span></span>

- `tagpath`

  <span data-ttu-id="41213-111">Cesta značek v `filename` , která vede k označení `name` .</span><span class="sxs-lookup"><span data-stu-id="41213-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="41213-112">Uzavřete cestu do jednoduchých uvozovek (' ').</span><span class="sxs-lookup"><span data-stu-id="41213-112">Enclose the path in single quotation marks (' ').</span></span>

- `name`

  <span data-ttu-id="41213-113">Specifikátor názvu ve značce, který předchází komentářům; `name`bude mít `id` .</span><span class="sxs-lookup"><span data-stu-id="41213-113">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>

- `id`

<span data-ttu-id="41213-114">ID značky, která předchází komentář.</span><span class="sxs-lookup"><span data-stu-id="41213-114">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="41213-115">ID uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="41213-115">Enclose the ID in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="41213-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41213-116">Remarks</span></span>

<span data-ttu-id="41213-117">`<include>`Značka vám umožní odkazovat na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="41213-117">The `<include>` tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="41213-118">Toto je alternativa k umístění dokumentačních komentářů přímo do souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="41213-118">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="41213-119">Vložením dokumentace do samostatného souboru můžete použít správu zdrojového kódu v dokumentaci samostatně ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="41213-119">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="41213-120">Je možné, že soubor zdrojového kódu je zarezervován a někdo jiný může mít zarezervován soubor dokumentace.</span><span class="sxs-lookup"><span data-stu-id="41213-120">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>

<span data-ttu-id="41213-121">`<include>`Značka používá syntaxi XPath XML.</span><span class="sxs-lookup"><span data-stu-id="41213-121">The `<include>` tag uses the XML XPath syntax.</span></span> <span data-ttu-id="41213-122">Způsoby přizpůsobení použití naleznete v dokumentaci XPath `<include>` .</span><span class="sxs-lookup"><span data-stu-id="41213-122">Refer to XPath documentation for ways to customize your `<include>` use.</span></span>

## <a name="example"></a><span data-ttu-id="41213-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="41213-123">Example</span></span>

<span data-ttu-id="41213-124">Toto je příklad vícesouborového typu.</span><span class="sxs-lookup"><span data-stu-id="41213-124">This is a multifile example.</span></span> <span data-ttu-id="41213-125">Následuje první soubor, který používá `<include>` .</span><span class="sxs-lookup"><span data-stu-id="41213-125">The following is the first file, which uses `<include>`.</span></span>

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

<span data-ttu-id="41213-126">Druhý soubor, *xml_include_tag.doc*, obsahuje následující dokumentační komentáře.</span><span class="sxs-lookup"><span data-stu-id="41213-126">The second file, *xml_include_tag.doc*, contains the following documentation comments.</span></span>

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

## <a name="program-output"></a><span data-ttu-id="41213-127">Výstup programu</span><span class="sxs-lookup"><span data-stu-id="41213-127">Program output</span></span>

<span data-ttu-id="41213-128">Následující výstup je generován při kompilaci třídy test a Test2 pomocí následujícího příkazového řádku: `-doc:DocFileName.xml.` v aplikaci Visual Studio zadáte možnost komentáře k dokumentu XML v podokně sestavení Návrháře projektu.</span><span class="sxs-lookup"><span data-stu-id="41213-128">The following output is generated when you compile the Test and Test2 classes with the following command line: `-doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="41213-129">Když kompilátor jazyka C# uvidí `<include>` značku, vyhledá v *xml_include_tag.doc* komentáře k dokumentaci místo aktuálního zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="41213-129">When the C# compiler sees the `<include>` tag, it searches for documentation comments in *xml_include_tag.doc* instead of the current source file.</span></span> <span data-ttu-id="41213-130">Kompilátor potom vygeneruje *DocFileName.xml*a jedná se o soubor, který je využíván nástroji dokumentace, jako je [Sandcastle](https://github.com/EWSoftware/SHFB) , k vytvoření konečné dokumentace.</span><span class="sxs-lookup"><span data-stu-id="41213-130">The compiler then generates *DocFileName.xml*, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="41213-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41213-131">See also</span></span>

- [<span data-ttu-id="41213-132">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="41213-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="41213-133">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="41213-133">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)

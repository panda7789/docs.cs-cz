---
title: <include> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 1e3722cbed02775d0ad4f392840ea10275c96be1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793434"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="4ed28-102">\<zahrnout > (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="4ed28-102">\<include> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ed28-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ed28-103">Syntax</span></span>

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a><span data-ttu-id="4ed28-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ed28-104">Parameters</span></span>

- `filename`

  <span data-ttu-id="4ed28-105">Název souboru XML, který obsahuje dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4ed28-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="4ed28-106">Název souboru může být kvalifikován cestou relativní k souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4ed28-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="4ed28-107">Uzavřete `filename` do jednoduchých uvozovek (' ').</span><span class="sxs-lookup"><span data-stu-id="4ed28-107">Enclose `filename` in single quotation marks (' ').</span></span>

- `tagpath`

  <span data-ttu-id="4ed28-108">Cesta značek v `filename`, které vedou k `name`značky</span><span class="sxs-lookup"><span data-stu-id="4ed28-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="4ed28-109">Uzavřete cestu do jednoduchých uvozovek (' ').</span><span class="sxs-lookup"><span data-stu-id="4ed28-109">Enclose the path in single quotation marks (' ').</span></span>

- `name`

  <span data-ttu-id="4ed28-110">Specifikátor názvu ve značce, který předchází komentářům; `name` bude mít `id`.</span><span class="sxs-lookup"><span data-stu-id="4ed28-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>

- `id`

<span data-ttu-id="4ed28-111">ID značky, která předchází komentář.</span><span class="sxs-lookup"><span data-stu-id="4ed28-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="4ed28-112">ID uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="4ed28-112">Enclose the ID in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="4ed28-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ed28-113">Remarks</span></span>

<span data-ttu-id="4ed28-114">\<include > umožňuje odkazování na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4ed28-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="4ed28-115">Toto je alternativa k umístění dokumentačních komentářů přímo do souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4ed28-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="4ed28-116">Vložením dokumentace do samostatného souboru můžete použít správu zdrojového kódu v dokumentaci samostatně ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4ed28-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="4ed28-117">Je možné, že soubor zdrojového kódu je zarezervován a někdo jiný může mít zarezervován soubor dokumentace.</span><span class="sxs-lookup"><span data-stu-id="4ed28-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>

<span data-ttu-id="4ed28-118">\<obsahuje značku > používá syntaxi XPath XML.</span><span class="sxs-lookup"><span data-stu-id="4ed28-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="4ed28-119">V dokumentaci XPath najdete způsoby přizpůsobení \<zahrnutí > použití.</span><span class="sxs-lookup"><span data-stu-id="4ed28-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>

## <a name="example"></a><span data-ttu-id="4ed28-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ed28-120">Example</span></span>

<span data-ttu-id="4ed28-121">Toto je příklad vícesouborového typu.</span><span class="sxs-lookup"><span data-stu-id="4ed28-121">This is a multifile example.</span></span> <span data-ttu-id="4ed28-122">Následuje první soubor, který používá \<include >.</span><span class="sxs-lookup"><span data-stu-id="4ed28-122">The following is the first file, which uses \<include>.</span></span>

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

<span data-ttu-id="4ed28-123">Druhý soubor *xml_include_tag. doc*obsahuje následující komentáře k dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4ed28-123">The second file, *xml_include_tag.doc*, contains the following documentation comments.</span></span>

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

## <a name="program-output"></a><span data-ttu-id="4ed28-124">Výstup programu</span><span class="sxs-lookup"><span data-stu-id="4ed28-124">Program output</span></span>

<span data-ttu-id="4ed28-125">Následující výstup je generován při kompilaci třídy test a Test2 pomocí následujícího příkazového řádku: `-doc:DocFileName.xml.` v aplikaci Visual Studio, zadáte možnost komentáře k dokumentu XML v podokně sestavení v Návrháři projektu.</span><span class="sxs-lookup"><span data-stu-id="4ed28-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `-doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="4ed28-126">Když C# kompilátor uvidí \<obsahuje značku >, vyhledá dokumentační komentáře v xml_include_tag. doc namísto aktuálního zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="4ed28-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="4ed28-127">Kompilátor pak vygeneruje DocFileName. XML a jedná se o soubor, který je využíván nástroji dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) , k vytvoření konečné dokumentace.</span><span class="sxs-lookup"><span data-stu-id="4ed28-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ed28-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ed28-128">See also</span></span>

- [<span data-ttu-id="4ed28-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4ed28-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4ed28-130">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="4ed28-130">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)

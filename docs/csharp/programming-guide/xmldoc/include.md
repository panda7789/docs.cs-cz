---
title: <include> – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 26241dab70a3b6a0cf80b374868fa759647cd8d9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587997"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="4cf77-102">\<zahrnout > (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="4cf77-102">\<include> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="4cf77-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cf77-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cf77-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cf77-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="4cf77-105">Název souboru XML, který obsahuje dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4cf77-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="4cf77-106">Název souboru může být kvalifikován cestou relativní k souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4cf77-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="4cf77-107">`filename` Uzavřete do jednoduchých uvozovek (' ').</span><span class="sxs-lookup"><span data-stu-id="4cf77-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="4cf77-108">Cesta značek v `filename` , která vede k označení `name`.</span><span class="sxs-lookup"><span data-stu-id="4cf77-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="4cf77-109">Uzavřete cestu do jednoduchých uvozovek (' ').</span><span class="sxs-lookup"><span data-stu-id="4cf77-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="4cf77-110">Specifikátor názvu ve značce, který předchází komentářům; `name` bude`id`mít.</span><span class="sxs-lookup"><span data-stu-id="4cf77-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="4cf77-111">ID značky, která předchází komentář.</span><span class="sxs-lookup"><span data-stu-id="4cf77-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="4cf77-112">ID uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="4cf77-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cf77-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4cf77-113">Remarks</span></span>  
 <span data-ttu-id="4cf77-114">Tag \<include > umožňuje odkazování na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4cf77-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="4cf77-115">Toto je alternativa k umístění dokumentačních komentářů přímo do souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4cf77-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="4cf77-116">Vložením dokumentace do samostatného souboru můžete použít správu zdrojového kódu v dokumentaci samostatně ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4cf77-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="4cf77-117">Je možné, že soubor zdrojového kódu je zarezervován a někdo jiný může mít zarezervován soubor dokumentace.</span><span class="sxs-lookup"><span data-stu-id="4cf77-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="4cf77-118">Tag \<include > používá syntaxi XPath XML.</span><span class="sxs-lookup"><span data-stu-id="4cf77-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="4cf77-119">V dokumentaci XPath najdete způsoby přizpůsobení \<použití > zahrnutí.</span><span class="sxs-lookup"><span data-stu-id="4cf77-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cf77-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cf77-120">Example</span></span>  
 <span data-ttu-id="4cf77-121">Toto je příklad vícesouborového typu.</span><span class="sxs-lookup"><span data-stu-id="4cf77-121">This is a multifile example.</span></span> <span data-ttu-id="4cf77-122">První soubor, který používá \<> include, je uveden níže:</span><span class="sxs-lookup"><span data-stu-id="4cf77-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 [!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]  
  
 <span data-ttu-id="4cf77-123">Druhý soubor xml_include_tag. doc obsahuje následující dokumentační dokumentaci:</span><span class="sxs-lookup"><span data-stu-id="4cf77-123">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
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
  
## <a name="program-output"></a><span data-ttu-id="4cf77-124">Výstup programu</span><span class="sxs-lookup"><span data-stu-id="4cf77-124">Program Output</span></span>  
 <span data-ttu-id="4cf77-125">Následující výstup je generován při kompilaci třídy test a Test2 pomocí následujícího příkazového řádku: `/doc:DocFileName.xml.`V aplikaci Visual Studio zadáte možnost komentáře k dokumentu XML v podokně sestavení v Návrháři projektu.</span><span class="sxs-lookup"><span data-stu-id="4cf77-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="4cf77-126">Když C# kompilátor uvidí \<značku include >, vyhledá komentáře k dokumentaci v souboru xml_include_tag. doc namísto aktuálního zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="4cf77-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="4cf77-127">Kompilátor pak vygeneruje DocFileName. XML a jedná se o soubor, který je využíván nástroji dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) , k vytvoření konečné dokumentace.</span><span class="sxs-lookup"><span data-stu-id="4cf77-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4cf77-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cf77-128">See also</span></span>

- [<span data-ttu-id="4cf77-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4cf77-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4cf77-130">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="4cf77-130">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)

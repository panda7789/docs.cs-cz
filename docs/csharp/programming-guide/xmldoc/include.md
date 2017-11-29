---
title: "&lt;zahrnout&gt; (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f4df6a23b2fe33b2390aef86891aedc6b04e464d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltincludegt-c-programming-guide"></a><span data-ttu-id="74096-102">&lt;zahrnout&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="74096-102">&lt;include&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="74096-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74096-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74096-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="74096-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="74096-105">Název souboru XML, který obsahuje v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="74096-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="74096-106">Název souboru může být kvalifikovaný s cestou.</span><span class="sxs-lookup"><span data-stu-id="74096-106">The file name can be qualified with a path.</span></span> <span data-ttu-id="74096-107">Uzavřete `filename` v jednoduchých uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="74096-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="74096-108">Cesta značky v `filename` který vede ke značce `name`.</span><span class="sxs-lookup"><span data-stu-id="74096-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="74096-109">Vložte cestu do jednoduchých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="74096-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="74096-110">Specifikátor název ve značce, která předchází komentáře; `name` bude mít `id`.</span><span class="sxs-lookup"><span data-stu-id="74096-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="74096-111">ID značky, která předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="74096-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="74096-112">Uzavřete ID do dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="74096-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74096-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74096-113">Remarks</span></span>  
 <span data-ttu-id="74096-114">\<Zahrnují > značka umožňuje odkazovat komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="74096-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="74096-115">Jde o alternativu k uvedení dokumentační komentáře ve zdrojovém kódu souboru přímo.</span><span class="sxs-lookup"><span data-stu-id="74096-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="74096-116">V dokumentaci k umístěním v samostatném souboru, můžete použít zdrojového kódu v dokumentaci k samostatně z zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="74096-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="74096-117">Jedna osoba může mít přístup k souboru zdrojového kódu rezervovaný, a souborů dokumentace rezervována může mít někdo jiný.</span><span class="sxs-lookup"><span data-stu-id="74096-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="74096-118">\<Zahrnují > Značka se používá syntaxe XML XPath.</span><span class="sxs-lookup"><span data-stu-id="74096-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="74096-119">Výraz XPath dokumentaci k tom, jak přizpůsobit vaší \<zahrnují > použít.</span><span class="sxs-lookup"><span data-stu-id="74096-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74096-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="74096-120">Example</span></span>  
 <span data-ttu-id="74096-121">Toto je příklad více souborů.</span><span class="sxs-lookup"><span data-stu-id="74096-121">This is a multifile example.</span></span> <span data-ttu-id="74096-122">První soubor, který používá \<zahrnují >, je uvedený níže:</span><span class="sxs-lookup"><span data-stu-id="74096-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 [!code-csharp[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 <span data-ttu-id="74096-123">Druhý soubor, xml_include_tag.doc, obsahuje následující dokumentační komentáře:</span><span class="sxs-lookup"><span data-stu-id="74096-123">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
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
  
## <a name="program-output"></a><span data-ttu-id="74096-124">Výstup programu</span><span class="sxs-lookup"><span data-stu-id="74096-124">Program Output</span></span>  
 <span data-ttu-id="74096-125">Tento výstup se vygeneruje, když kompilujete Test a Test2 tříd pomocí následující příkazový řádek: `/doc:DocFileName.xml.` v sadě Visual Studio, zadejte možnost komentáře doc XML v podokně sestavení v Návrháři projektu.</span><span class="sxs-lookup"><span data-stu-id="74096-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="74096-126">Když uvidí kompilátor jazyka C# \<zahrnují > značky, bude hledat pro dokumentační komentáře ve xml_include_tag.doc místo aktuální zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="74096-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="74096-127">Kompilátor pak vygeneruje DocFileName.xml, a to je soubor, který využívá dokumentace nástroje, jako [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB) k vytvoření konečné dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="74096-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74096-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="74096-128">See Also</span></span>  
 [<span data-ttu-id="74096-129">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="74096-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="74096-130">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="74096-130">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

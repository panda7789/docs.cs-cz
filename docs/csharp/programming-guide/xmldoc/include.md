---
title: '&lt;zahrnout&gt; (C# Programming Guide)'
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 854c8b61fa8164bccfc9451f2f163dab4a56388f
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360489"
---
# <a name="ltincludegt-c-programming-guide"></a><span data-ttu-id="3dfec-102">&lt;zahrnout&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="3dfec-102">&lt;include&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="3dfec-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dfec-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3dfec-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="3dfec-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="3dfec-105">Název souboru XML, který obsahuje dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="3dfec-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="3dfec-106">Název souboru může být kvalifikovány s cestou relativní k souboru se zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="3dfec-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="3dfec-107">Uzavřete `filename` v jednoduchých uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="3dfec-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="3dfec-108">Cesta klíčových slov do `filename` , který vede ke značce `name`.</span><span class="sxs-lookup"><span data-stu-id="3dfec-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="3dfec-109">Vložte cestu do jednoduchých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="3dfec-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="3dfec-110">Specifikátor názvem ve značce, který předchází komentáře; `name` bude mít `id`.</span><span class="sxs-lookup"><span data-stu-id="3dfec-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="3dfec-111">ID značky, které předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="3dfec-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="3dfec-112">ID uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="3dfec-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dfec-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3dfec-113">Remarks</span></span>  
 <span data-ttu-id="3dfec-114">\<Zahrnout > značky umožňuje odkazovat na komentáře do jiného souboru, které popisují typy a členy ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="3dfec-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="3dfec-115">Jedná se o alternativu k uvedení dokumentační komentáře přímo v souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="3dfec-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="3dfec-116">Vložením dokumentaci v samostatném souboru můžete použít správy zdrojového kódu v dokumentaci samostatně ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="3dfec-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="3dfec-117">Jedna osoba může mít souboru se zdrojovým kódem rezervovat a někdo jiný může mít soubor dokumentace rezervován.</span><span class="sxs-lookup"><span data-stu-id="3dfec-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="3dfec-118">\<Zahrnout > značky používá syntaxe jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="3dfec-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="3dfec-119">XPath dokumentaci pro přizpůsobení vaší \<zahrnout > použít.</span><span class="sxs-lookup"><span data-stu-id="3dfec-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dfec-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="3dfec-120">Example</span></span>  
 <span data-ttu-id="3dfec-121">Toto je vícesouborové příklad.</span><span class="sxs-lookup"><span data-stu-id="3dfec-121">This is a multifile example.</span></span> <span data-ttu-id="3dfec-122">První soubor, který používá \<zahrnout >, která jsou uvedená níže:</span><span class="sxs-lookup"><span data-stu-id="3dfec-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 [!code-csharp[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 <span data-ttu-id="3dfec-123">Druhý soubor, xml_include_tag.doc, obsahuje následující komentáře k dokumentaci:</span><span class="sxs-lookup"><span data-stu-id="3dfec-123">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
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
  
## <a name="program-output"></a><span data-ttu-id="3dfec-124">Výstup programu</span><span class="sxs-lookup"><span data-stu-id="3dfec-124">Program Output</span></span>  
 <span data-ttu-id="3dfec-125">Následující výstup je generována, když kompilujete třídy testu a Test2 s následujícím příkazovým řádkem: `/doc:DocFileName.xml.` v sadě Visual Studio, můžete zadat možnost komentáře dokumentu XML v podokně sestavení Návrháře projektu.</span><span class="sxs-lookup"><span data-stu-id="3dfec-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="3dfec-126">Když kompilátor jazyka C# narazí \<zahrnout > značky, budou vyhledány dokumentační komentáře ve xml_include_tag.doc namísto aktuálního zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="3dfec-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="3dfec-127">Kompilátor poté vygeneruje DocFileName.xml a jedná se o soubor, který je využívána dokumentace nástroje, jako například [Sandcastle](https://github.com/EWSoftware/SHFB) vytvořit finální dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="3dfec-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3dfec-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dfec-128">See Also</span></span>

- [<span data-ttu-id="3dfec-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3dfec-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3dfec-130">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="3dfec-130">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

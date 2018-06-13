---
title: '&lt;zahrnout&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 65bc0439696612cd8331a9c0718efcfee83af574
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602733"
---
# <a name="ltincludegt-visual-basic"></a><span data-ttu-id="0d5be-102">&lt;zahrnout&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d5be-102">&lt;include&gt; (Visual Basic)</span></span>
<span data-ttu-id="0d5be-103">Odkazuje na jiný soubor, který popisuje typy a členy ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="0d5be-103">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d5be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d5be-104">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d5be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d5be-105">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="0d5be-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0d5be-106">Required.</span></span> <span data-ttu-id="0d5be-107">Název souboru, který obsahuje v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="0d5be-107">The name of the file containing the documentation.</span></span> <span data-ttu-id="0d5be-108">Název souboru může být kvalifikovaný s cestou.</span><span class="sxs-lookup"><span data-stu-id="0d5be-108">The file name can be qualified with a path.</span></span> <span data-ttu-id="0d5be-109">Uzavřete `filename` v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="0d5be-109">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="0d5be-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0d5be-110">Required.</span></span> <span data-ttu-id="0d5be-111">Cesta značky v `filename` který vede ke značce `name`.</span><span class="sxs-lookup"><span data-stu-id="0d5be-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="0d5be-112">Vložte cestu do dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="0d5be-112">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="0d5be-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0d5be-113">Required.</span></span> <span data-ttu-id="0d5be-114">Specifikátor název ve značce, která předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="0d5be-114">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="0d5be-115">`Name` bude mít `id`.</span><span class="sxs-lookup"><span data-stu-id="0d5be-115">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="0d5be-116">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0d5be-116">Required.</span></span> <span data-ttu-id="0d5be-117">ID značky, která předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="0d5be-117">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="0d5be-118">Uzavřete ID v jednoduchých uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="0d5be-118">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d5be-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d5be-119">Remarks</span></span>  
 <span data-ttu-id="0d5be-120">Použití `<include>` značky k odkazování na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="0d5be-120">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="0d5be-121">Jde o alternativu k uvedení dokumentační komentáře ve zdrojovém kódu souboru přímo.</span><span class="sxs-lookup"><span data-stu-id="0d5be-121">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="0d5be-122">`<include>` Značku používá doporučení W3C XML Path Language (XPath) verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="0d5be-122">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="0d5be-123">Další informace o tom, jak přizpůsobit vaší `<include>` použijte je k dispozici na http://www.w3.org/TR/xpath.</span><span class="sxs-lookup"><span data-stu-id="0d5be-123">More information for ways to customize your `<include>` use is available at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d5be-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d5be-124">Example</span></span>  
 <span data-ttu-id="0d5be-125">Tento příklad používá `<include>` značka import člen dokumentační komentáře ze souboru s názvem `commentFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="0d5be-125">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 <span data-ttu-id="0d5be-126">Formát `commentFile.xml` je následující.</span><span class="sxs-lookup"><span data-stu-id="0d5be-126">The format of the `commentFile.xml` is as follows.</span></span>  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d5be-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d5be-127">See Also</span></span>  
 [<span data-ttu-id="0d5be-128">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="0d5be-128">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

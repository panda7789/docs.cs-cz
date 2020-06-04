---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 78a10624107cea349b01f484c641190a945dbd7e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400108"
---
# <a name="include-visual-basic"></a><span data-ttu-id="7de0c-101">\<include> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7de0c-101">\<include> (Visual Basic)</span></span>
<span data-ttu-id="7de0c-102">Odkazuje na jiný soubor, který popisuje typy a členy ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="7de0c-102">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7de0c-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7de0c-103">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="7de0c-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="7de0c-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="7de0c-105">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7de0c-105">Required.</span></span> <span data-ttu-id="7de0c-106">Název souboru, který obsahuje dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="7de0c-106">The name of the file containing the documentation.</span></span> <span data-ttu-id="7de0c-107">Název souboru může být kvalifikován cestou.</span><span class="sxs-lookup"><span data-stu-id="7de0c-107">The file name can be qualified with a path.</span></span> <span data-ttu-id="7de0c-108">Uzavřete `filename` do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="7de0c-108">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="7de0c-109">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7de0c-109">Required.</span></span> <span data-ttu-id="7de0c-110">Cesta značek v `filename` , která vede k označení `name` .</span><span class="sxs-lookup"><span data-stu-id="7de0c-110">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="7de0c-111">Uzavřete cestu do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="7de0c-111">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="7de0c-112">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7de0c-112">Required.</span></span> <span data-ttu-id="7de0c-113">Specifikátor názvu ve značce, který předchází komentář.</span><span class="sxs-lookup"><span data-stu-id="7de0c-113">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="7de0c-114">`Name`bude mít `id` .</span><span class="sxs-lookup"><span data-stu-id="7de0c-114">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="7de0c-115">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7de0c-115">Required.</span></span> <span data-ttu-id="7de0c-116">ID značky, která předchází komentář.</span><span class="sxs-lookup"><span data-stu-id="7de0c-116">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="7de0c-117">Uveďte ID v jednoduchých uvozovkách (' ').</span><span class="sxs-lookup"><span data-stu-id="7de0c-117">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7de0c-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7de0c-118">Remarks</span></span>  
 <span data-ttu-id="7de0c-119">Použijte `<include>` značku pro odkazování na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="7de0c-119">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="7de0c-120">Toto je alternativa k umístění dokumentačních komentářů přímo do souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="7de0c-120">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="7de0c-121">`<include>`Značka používá doporučení jazyka W3C XML Path (XPath) verze 1,0.</span><span class="sxs-lookup"><span data-stu-id="7de0c-121">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="7de0c-122">Další informace o způsobech přizpůsobení `<include>` použití naleznete v tématu <https://www.w3.org/TR/xpath> .</span><span class="sxs-lookup"><span data-stu-id="7de0c-122">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7de0c-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="7de0c-123">Example</span></span>  
 <span data-ttu-id="7de0c-124">Tento příklad používá `<include>` značku k importu komentářů k dokumentaci členů ze souboru s názvem `commentFile.xml` .</span><span class="sxs-lookup"><span data-stu-id="7de0c-124">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="7de0c-125">Formát `commentFile.xml` je následující:</span><span class="sxs-lookup"><span data-stu-id="7de0c-125">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7de0c-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7de0c-126">See also</span></span>

- [<span data-ttu-id="7de0c-127">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="7de0c-127">XML Comment Tags</span></span>](index.md)

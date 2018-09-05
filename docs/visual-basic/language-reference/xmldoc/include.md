---
title: '&lt;zahrnout&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: da7a6c15c558fc56dbc6a874d4a28c4434f67668
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671951"
---
# <a name="ltincludegt-visual-basic"></a><span data-ttu-id="9d242-102">&lt;zahrnout&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d242-102">&lt;include&gt; (Visual Basic)</span></span>
<span data-ttu-id="9d242-103">Odkazuje na jiný soubor, který popisuje typy a členy ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="9d242-103">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d242-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d242-104">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d242-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d242-105">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="9d242-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9d242-106">Required.</span></span> <span data-ttu-id="9d242-107">Název souboru, který obsahuje dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="9d242-107">The name of the file containing the documentation.</span></span> <span data-ttu-id="9d242-108">Název souboru může být kvalifikovány s cestou.</span><span class="sxs-lookup"><span data-stu-id="9d242-108">The file name can be qualified with a path.</span></span> <span data-ttu-id="9d242-109">Uzavřete `filename` do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="9d242-109">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="9d242-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9d242-110">Required.</span></span> <span data-ttu-id="9d242-111">Cesta klíčových slov do `filename` , který vede ke značce `name`.</span><span class="sxs-lookup"><span data-stu-id="9d242-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="9d242-112">Vložte cestu do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="9d242-112">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="9d242-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9d242-113">Required.</span></span> <span data-ttu-id="9d242-114">Specifikátor názvem ve značce, který předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="9d242-114">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="9d242-115">`Name` bude mít `id`.</span><span class="sxs-lookup"><span data-stu-id="9d242-115">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="9d242-116">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9d242-116">Required.</span></span> <span data-ttu-id="9d242-117">ID značky, které předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="9d242-117">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="9d242-118">ID uzavřete do jednoduchých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="9d242-118">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d242-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d242-119">Remarks</span></span>  
 <span data-ttu-id="9d242-120">Použití `<include>` značka, které odkazují na komentáře do jiného souboru, které popisují typy a členy ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="9d242-120">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="9d242-121">Jedná se o alternativu k uvedení dokumentační komentáře přímo v souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="9d242-121">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="9d242-122">`<include>` Značky používá doporučení W3C jazyk XML Path (XPath) verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="9d242-122">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="9d242-123">Další informace o tom, jak přizpůsobit vaší `<include>` použijte je k dispozici na http://www.w3.org/TR/xpath.</span><span class="sxs-lookup"><span data-stu-id="9d242-123">More information for ways to customize your `<include>` use is available at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d242-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d242-124">Example</span></span>  
 <span data-ttu-id="9d242-125">V tomto příkladu `<include>` značka Import ze souboru s názvem člena dokumentační komentáře `commentFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="9d242-125">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 <span data-ttu-id="9d242-126">Formát `commentFile.xml` vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="9d242-126">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d242-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d242-127">See Also</span></span>  
 [<span data-ttu-id="9d242-128">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="9d242-128">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

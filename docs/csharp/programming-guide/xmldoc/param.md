---
title: <param> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 08b5257cedfcaf6fe34b8218dda93163d4c0d98b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976678"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="896c0-102">\<Param > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="896c0-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="896c0-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="896c0-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="896c0-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="896c0-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="896c0-105">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="896c0-105">The name of a method parameter.</span></span> <span data-ttu-id="896c0-106">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="896c0-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="896c0-107">Popis pro parametr.</span><span class="sxs-lookup"><span data-stu-id="896c0-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="896c0-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="896c0-108">Remarks</span></span>  
 <span data-ttu-id="896c0-109">\<Param > značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="896c0-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="896c0-110">Do dokumentu více parametrů, použijte více \<param > značky.</span><span class="sxs-lookup"><span data-stu-id="896c0-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="896c0-111">Text \<param > značky se zobrazí v IntelliSense, prohlížeči objektů a v sestavě webového kódu komentář.</span><span class="sxs-lookup"><span data-stu-id="896c0-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="896c0-112">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="896c0-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="896c0-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="896c0-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="896c0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="896c0-114">See also</span></span>

- [<span data-ttu-id="896c0-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="896c0-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="896c0-116">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="896c0-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

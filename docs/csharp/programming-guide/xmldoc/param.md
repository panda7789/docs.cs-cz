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
ms.openlocfilehash: ffa3bd066ce753f2b953f2d6d0a70a3bf65293ff
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468029"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="db80a-102">\<Param > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="db80a-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="db80a-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db80a-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="db80a-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="db80a-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="db80a-105">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="db80a-105">The name of a method parameter.</span></span> <span data-ttu-id="db80a-106">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="db80a-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="db80a-107">Popis pro parametr.</span><span class="sxs-lookup"><span data-stu-id="db80a-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db80a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db80a-108">Remarks</span></span>  
 <span data-ttu-id="db80a-109">\<Param > značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="db80a-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="db80a-110">Do dokumentu více parametrů, použijte více \<param > značky.</span><span class="sxs-lookup"><span data-stu-id="db80a-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="db80a-111">Text \<param > značky se zobrazí v IntelliSense, prohlížeči objektů a v sestavě webového kódu komentář.</span><span class="sxs-lookup"><span data-stu-id="db80a-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="db80a-112">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="db80a-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db80a-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="db80a-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="db80a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db80a-114">See also</span></span>

- [<span data-ttu-id="db80a-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="db80a-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="db80a-116">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="db80a-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

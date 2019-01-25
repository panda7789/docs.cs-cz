---
title: '&lt;Param&gt; - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: fb31e1d4c39888765fe3e55674d5b6d18b9d5b65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641015"
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="a8a9e-102">&lt;Param&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="a8a9e-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="a8a9e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8a9e-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8a9e-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8a9e-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a8a9e-105">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="a8a9e-105">The name of a method parameter.</span></span> <span data-ttu-id="a8a9e-106">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="a8a9e-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="a8a9e-107">Popis pro parametr.</span><span class="sxs-lookup"><span data-stu-id="a8a9e-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8a9e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8a9e-108">Remarks</span></span>  
 <span data-ttu-id="a8a9e-109">\<Param > značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="a8a9e-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="a8a9e-110">Do dokumentu více parametrů, použijte více \<param > značky.</span><span class="sxs-lookup"><span data-stu-id="a8a9e-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="a8a9e-111">Text \<param > značky se zobrazí v IntelliSense, prohlížeči objektů a v sestavě webového kódu komentář.</span><span class="sxs-lookup"><span data-stu-id="a8a9e-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="a8a9e-112">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="a8a9e-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8a9e-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8a9e-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a8a9e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8a9e-114">See also</span></span>

- [<span data-ttu-id="a8a9e-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a8a9e-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a8a9e-116">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="a8a9e-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

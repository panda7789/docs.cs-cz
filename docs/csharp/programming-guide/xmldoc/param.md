---
title: '&lt;Param&gt; (C# Programming Guide)'
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: b4afa84aadc68ca2f0113023319f02a10dc17836
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508212"
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="6ac56-102">&lt;Param&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="6ac56-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="6ac56-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ac56-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ac56-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ac56-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6ac56-105">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="6ac56-105">The name of a method parameter.</span></span> <span data-ttu-id="6ac56-106">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="6ac56-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="6ac56-107">Popis pro parametr.</span><span class="sxs-lookup"><span data-stu-id="6ac56-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ac56-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ac56-108">Remarks</span></span>  
 <span data-ttu-id="6ac56-109">\<Param > značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="6ac56-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="6ac56-110">Do dokumentu více parametrů, použijte více \<param > značky.</span><span class="sxs-lookup"><span data-stu-id="6ac56-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="6ac56-111">Text \<param > značky se zobrazí v IntelliSense, prohlížeči objektů a v sestavě webového kódu komentář.</span><span class="sxs-lookup"><span data-stu-id="6ac56-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="6ac56-112">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="6ac56-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ac56-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ac56-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6ac56-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ac56-114">See Also</span></span>

- [<span data-ttu-id="6ac56-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6ac56-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6ac56-116">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="6ac56-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

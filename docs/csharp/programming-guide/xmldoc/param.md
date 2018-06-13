---
title: '&lt;Param&gt; (C# Průvodce programováním)'
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 3d89637e5b1238c582390750e8eef30960fa90b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338010"
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="275a2-102">&lt;Param&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="275a2-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="275a2-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="275a2-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="275a2-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="275a2-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="275a2-105">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="275a2-105">The name of a method parameter.</span></span> <span data-ttu-id="275a2-106">Uzavřete název do dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="275a2-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="275a2-107">Popis parametru.</span><span class="sxs-lookup"><span data-stu-id="275a2-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="275a2-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="275a2-108">Remarks</span></span>  
 <span data-ttu-id="275a2-109">\<Param > Značka je třeba používat v komentář pro deklaraci metody k popisu jeden z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="275a2-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="275a2-110">K dokumentu několik parametrů, použijte více \<param > značky.</span><span class="sxs-lookup"><span data-stu-id="275a2-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="275a2-111">Text pro \<param > Značka se zobrazí v technologii IntelliSense, prohlížeč objektů a sestava webové komentář kódu.</span><span class="sxs-lookup"><span data-stu-id="275a2-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="275a2-112">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="275a2-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="275a2-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="275a2-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="275a2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="275a2-114">See Also</span></span>  
 [<span data-ttu-id="275a2-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="275a2-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="275a2-116">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="275a2-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

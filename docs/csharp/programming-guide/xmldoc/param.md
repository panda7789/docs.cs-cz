---
title: "&lt;Param&gt; (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a5325b91130623442c9cf5453e52418bb44cc34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="ec4d5-102">&lt;Param&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="ec4d5-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="ec4d5-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec4d5-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec4d5-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec4d5-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ec4d5-105">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="ec4d5-105">The name of a method parameter.</span></span> <span data-ttu-id="ec4d5-106">Uzavřete název do dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="ec4d5-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="ec4d5-107">Popis parametru.</span><span class="sxs-lookup"><span data-stu-id="ec4d5-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec4d5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec4d5-108">Remarks</span></span>  
 <span data-ttu-id="ec4d5-109">\<Param > Značka je třeba používat v komentář pro deklaraci metody k popisu jeden z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="ec4d5-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="ec4d5-110">K dokumentu několik parametrů, použijte více \<param > značky.</span><span class="sxs-lookup"><span data-stu-id="ec4d5-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="ec4d5-111">Text pro \<param > Značka se zobrazí v technologii IntelliSense, prohlížeč objektů a sestava webové komentář kódu.</span><span class="sxs-lookup"><span data-stu-id="ec4d5-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="ec4d5-112">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="ec4d5-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec4d5-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec4d5-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ec4d5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec4d5-114">See Also</span></span>  
 [<span data-ttu-id="ec4d5-115">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ec4d5-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ec4d5-116">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="ec4d5-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

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
ms.openlocfilehash: 3f1099da6a43ed7f48389a16e3be6a3b6b98a148
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271574"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="b7d83-102">\<Param > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="b7d83-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="b7d83-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7d83-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7d83-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7d83-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b7d83-105">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="b7d83-105">The name of a method parameter.</span></span> <span data-ttu-id="b7d83-106">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="b7d83-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="b7d83-107">Popis pro parametr.</span><span class="sxs-lookup"><span data-stu-id="b7d83-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7d83-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7d83-108">Remarks</span></span>  
 <span data-ttu-id="b7d83-109">\<Param > značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="b7d83-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="b7d83-110">Do dokumentu více parametrů, použijte více \<param > značky.</span><span class="sxs-lookup"><span data-stu-id="b7d83-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="b7d83-111">Text \<param > značky se zobrazí v IntelliSense, prohlížeči objektů a v sestavě webového kódu komentář.</span><span class="sxs-lookup"><span data-stu-id="b7d83-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="b7d83-112">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="b7d83-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7d83-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7d83-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b7d83-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7d83-114">See also</span></span>

- [<span data-ttu-id="b7d83-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b7d83-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b7d83-116">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="b7d83-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

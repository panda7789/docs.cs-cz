---
title: "&lt;typeparam&gt; (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e1b8800e39b1ee5eeac8c5d3e4390ed3226b33a3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="lttypeparamgt-c-programming-guide"></a><span data-ttu-id="6d529-102">&lt;typeparam&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="6d529-102">&lt;typeparam&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="6d529-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d529-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d529-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d529-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6d529-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="6d529-105">The name of the type parameter.</span></span> <span data-ttu-id="6d529-106">Uzavřete název do dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="6d529-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="6d529-107">Popis pro parametr typu.</span><span class="sxs-lookup"><span data-stu-id="6d529-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d529-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d529-108">Remarks</span></span>  
 <span data-ttu-id="6d529-109">`<typeparam>` Značky by měl být používány komentář pro obecný typ nebo metoda deklaraci k popisu parametr typu.</span><span class="sxs-lookup"><span data-stu-id="6d529-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="6d529-110">Přidání značky pro každý typ parametr obecného typu nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="6d529-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="6d529-111">Další informace najdete v tématu [obecné typy](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="6d529-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="6d529-112">Text pro `<typeparam>` značky se zobrazí v technologii IntelliSense, [okno prohlížeče objekt](http://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) sestava webové komentář kódu.</span><span class="sxs-lookup"><span data-stu-id="6d529-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](http://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) code comment web report.</span></span>  
  
 <span data-ttu-id="6d529-113">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="6d529-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d529-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d529-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6d529-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d529-115">See Also</span></span>  
 [<span data-ttu-id="6d529-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6d529-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6d529-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6d529-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6d529-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="6d529-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

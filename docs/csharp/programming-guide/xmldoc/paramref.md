---
title: "&lt;paramref&gt; (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fff532c02538f121ebe399e1780d8c19d9d6633a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltparamrefgt-c-programming-guide"></a><span data-ttu-id="5b41f-102">&lt;paramref&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="5b41f-102">&lt;paramref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="5b41f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b41f-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b41f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b41f-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5b41f-105">Název parametru, který bude odkazovat na.</span><span class="sxs-lookup"><span data-stu-id="5b41f-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="5b41f-106">Uzavřete název do dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="5b41f-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b41f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b41f-107">Remarks</span></span>  
 <span data-ttu-id="5b41f-108">\<Paramref > Značka poskytuje způsob, jak znamenat, že komentáře slovo v kódu, například v \<souhrnné > nebo \<Poznámky > bloku odkazuje na parametr.</span><span class="sxs-lookup"><span data-stu-id="5b41f-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="5b41f-109">K formátování slovo nějakým způsobem distinct, například s tučné a kurzíva písma lze zpracovat soubor XML.</span><span class="sxs-lookup"><span data-stu-id="5b41f-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="5b41f-110">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="5b41f-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b41f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b41f-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5b41f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b41f-112">See Also</span></span>  
 [<span data-ttu-id="5b41f-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="5b41f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5b41f-114">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="5b41f-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

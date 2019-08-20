---
title: <paramref>– C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: e442b6829859ebc4dce6a0f5b6cd6cb777ab1400
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587904"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="864b9-102">\<paramref > (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="864b9-102">\<paramref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="864b9-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="864b9-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="864b9-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="864b9-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="864b9-105">Název parametru, na který se má odkazovat</span><span class="sxs-lookup"><span data-stu-id="864b9-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="864b9-106">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="864b9-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="864b9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="864b9-107">Remarks</span></span>  
 <span data-ttu-id="864b9-108">Značka > \< \<paramref poskytuje způsob, jak označit, že slovo v komentářích kódu, například v souhrnném > nebo v > bloku, odkazuje na parametr. \<</span><span class="sxs-lookup"><span data-stu-id="864b9-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="864b9-109">Soubor XML lze zpracovat pro formátování tohoto slova nějakým způsobem, například tučným písmem nebo kurzívou.</span><span class="sxs-lookup"><span data-stu-id="864b9-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="864b9-110">Zkompilujte pomocí [/doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte dokumentační komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="864b9-110">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="864b9-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="864b9-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="864b9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="864b9-112">See also</span></span>

- [<span data-ttu-id="864b9-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="864b9-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="864b9-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="864b9-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)

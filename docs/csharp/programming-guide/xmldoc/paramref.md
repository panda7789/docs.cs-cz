---
title: <paramref> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 4fd0770bfe6c15c0e9b10239019ec265550dc372
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262832"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="ecd48-102">\<paramref > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="ecd48-102">\<paramref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="ecd48-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecd48-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecd48-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecd48-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ecd48-105">Název parametru jako reference.</span><span class="sxs-lookup"><span data-stu-id="ecd48-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="ecd48-106">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="ecd48-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecd48-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecd48-107">Remarks</span></span>  
 <span data-ttu-id="ecd48-108">\<Paramref > značky poskytuje způsob, jak určit, že slovo v kódu komentáře, například v \<summary > nebo \<Poznámky > bloku odkazuje na parametr.</span><span class="sxs-lookup"><span data-stu-id="ecd48-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="ecd48-109">Soubor XML mohou být zpracovány do naformátuje toto slovo distinct způsobem, jako tučný nebo kurzívu písma.</span><span class="sxs-lookup"><span data-stu-id="ecd48-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="ecd48-110">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="ecd48-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecd48-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecd48-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ecd48-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecd48-112">See also</span></span>

- [<span data-ttu-id="ecd48-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ecd48-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ecd48-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="ecd48-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

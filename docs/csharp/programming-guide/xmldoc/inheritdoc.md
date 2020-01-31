---
title: Průvodce C# programováním <inheritdoc>
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d660cb1739733c4e98ae0b7939476fe74e6cf200
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795159"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="4235b-102">\<inheritdoc > (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="4235b-102">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="4235b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4235b-103">Syntax</span></span>  
  
```xml  
<inheritdoc/> 
```  

## <a name="inheritdoc"></a><span data-ttu-id="4235b-104">InheritDoc</span><span class="sxs-lookup"><span data-stu-id="4235b-104">InheritDoc</span></span>

<span data-ttu-id="4235b-105">Zdědit komentáře XML ze základních tříd, rozhraní a podobných metod.</span><span class="sxs-lookup"><span data-stu-id="4235b-105">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="4235b-106">Tím se eliminuje nechtěné kopírování a vkládání duplicitních komentářů XML a automaticky se synchronizují komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="4235b-106">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span> 
  
## <a name="remarks"></a><span data-ttu-id="4235b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4235b-107">Remarks</span></span>  
<span data-ttu-id="4235b-108">Přidejte komentáře XML do základních tříd nebo rozhraní a umožněte InheritDoc kopírovat komentáře do implementací tříd.</span><span class="sxs-lookup"><span data-stu-id="4235b-108">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="4235b-109">Přidejte své komentáře XML do synchronních metod a umožněte InheritDoc kopírovat komentáře do asynchronních verzí stejných metod.</span><span class="sxs-lookup"><span data-stu-id="4235b-109">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="4235b-110">Pokud chcete kopírovat komentáře z konkrétního člena, můžete použít atribut `cref` k určení člena.</span><span class="sxs-lookup"><span data-stu-id="4235b-110">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="4235b-111">Příklady</span><span class="sxs-lookup"><span data-stu-id="4235b-111">Examples</span></span>
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="4235b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4235b-112">See also</span></span>

- [<span data-ttu-id="4235b-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4235b-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4235b-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="4235b-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)

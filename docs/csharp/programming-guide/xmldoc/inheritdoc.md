---
title: <inheritdoc>- Průvodce programováním jazyka C#
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 6f42462f21d045428577cd2123e2180d866f1e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156945"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="43151-102">\<inheritdoc> (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="43151-102">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="43151-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43151-103">Syntax</span></span>  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a><span data-ttu-id="43151-104">InheritDoc</span><span class="sxs-lookup"><span data-stu-id="43151-104">InheritDoc</span></span>

<span data-ttu-id="43151-105">Dědit xml komentáře ze základních tříd, rozhraní a podobné metody.</span><span class="sxs-lookup"><span data-stu-id="43151-105">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="43151-106">Tím se eliminuje nechtěné kopírování a vkládání duplicitních komentářů XML a automaticky udržuje komentáře XML synchronizované.</span><span class="sxs-lookup"><span data-stu-id="43151-106">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="43151-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43151-107">Remarks</span></span>  
<span data-ttu-id="43151-108">Přidejte komentáře XML do základních tříd nebo rozhraní a nechte InheritDoc zkopírovat komentáře do implementujících tříd.</span><span class="sxs-lookup"><span data-stu-id="43151-108">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="43151-109">Přidejte komentáře XML do synchronních metod a nechte InheritDoc zkopírovat komentáře do asynchronních verzí stejných metod.</span><span class="sxs-lookup"><span data-stu-id="43151-109">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="43151-110">Pokud chcete zkopírovat komentáře z určitého člena, můžete použít `cref` atribut k určení člena.</span><span class="sxs-lookup"><span data-stu-id="43151-110">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="43151-111">Příklady</span><span class="sxs-lookup"><span data-stu-id="43151-111">Examples</span></span>
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="43151-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="43151-112">See also</span></span>

- [<span data-ttu-id="43151-113">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="43151-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="43151-114">Doporučené značky pro komentáře k dokumentaci</span><span class="sxs-lookup"><span data-stu-id="43151-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)

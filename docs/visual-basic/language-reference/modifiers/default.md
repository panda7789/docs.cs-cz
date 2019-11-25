---
title: Výchozí
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: ad4c9528f208cc2c31f07b0506d1b049a7568c86
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351572"
---
# <a name="default-visual-basic"></a><span data-ttu-id="a63bd-102">Výchozí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a63bd-102">Default (Visual Basic)</span></span>
<span data-ttu-id="a63bd-103">Identifies a property as the default property of its class, structure, or interface.</span><span class="sxs-lookup"><span data-stu-id="a63bd-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a63bd-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a63bd-104">Remarks</span></span>  
 <span data-ttu-id="a63bd-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span><span class="sxs-lookup"><span data-stu-id="a63bd-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="a63bd-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span><span class="sxs-lookup"><span data-stu-id="a63bd-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="a63bd-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span><span class="sxs-lookup"><span data-stu-id="a63bd-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="a63bd-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span><span class="sxs-lookup"><span data-stu-id="a63bd-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="a63bd-109">This can lead to compiler errors or subtle run-time logic errors.</span><span class="sxs-lookup"><span data-stu-id="a63bd-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="a63bd-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span><span class="sxs-lookup"><span data-stu-id="a63bd-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="a63bd-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span><span class="sxs-lookup"><span data-stu-id="a63bd-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="a63bd-112">Because of these disadvantages, you should consider not defining default properties.</span><span class="sxs-lookup"><span data-stu-id="a63bd-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="a63bd-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span><span class="sxs-lookup"><span data-stu-id="a63bd-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="a63bd-114">The `Default` modifier can be used in this context:</span><span class="sxs-lookup"><span data-stu-id="a63bd-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="a63bd-115">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="a63bd-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a63bd-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a63bd-116">See also</span></span>

- [<span data-ttu-id="a63bd-117">How to: Declare and Call a Default Property in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a63bd-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="a63bd-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a63bd-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)

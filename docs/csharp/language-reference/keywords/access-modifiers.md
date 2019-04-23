---
title: Přístup k modifikátory - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: d87ea1ff18c4697a2c04f22cbf67720f21cbf459
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118128"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="fa1de-102">Modifikátory přístupu (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fa1de-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="fa1de-103">Modifikátory přístupu jsou klíčová slova používaná k určení je deklarovaná přístupnost člena nebo typu.</span><span class="sxs-lookup"><span data-stu-id="fa1de-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="fa1de-104">Tato část představuje čtyři přístupu modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="fa1de-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="fa1de-105">Následujících šest úrovní přístupu se dá nastavit pomocí přístupu modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="fa1de-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="fa1de-106">[`public`](public.md): Přístup není omezený.</span><span class="sxs-lookup"><span data-stu-id="fa1de-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="fa1de-107">[`protected`](protected.md): Přístup je omezený na obsahující třídu nebo typy odvozené od třídy obsahující.</span><span class="sxs-lookup"><span data-stu-id="fa1de-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="fa1de-108">[`internal`](internal.md): Přístup je omezený na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa1de-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="fa1de-109">[`protected internal`](protected-internal.md): Přístup je omezený na aktuální sestavení nebo typy odvozené od třídy obsahující.</span><span class="sxs-lookup"><span data-stu-id="fa1de-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="fa1de-110">[`private`](private.md): Přístup je omezený na nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="fa1de-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="fa1de-111">[`private protected`](private-protected.md): Přístup je omezený na obsahující třídu nebo typy odvozené od třídy obsahující v rámci aktuálního sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa1de-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="fa1de-112">Tato část představuje také následující:</span><span class="sxs-lookup"><span data-stu-id="fa1de-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="fa1de-113">[Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md): Chcete-li deklarovat šest úrovní usnadnění přístupu pomocí čtyř přístupu modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="fa1de-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="fa1de-114">[Doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md): Určuje, kde v částech programu může být odkazováno člena.</span><span class="sxs-lookup"><span data-stu-id="fa1de-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="fa1de-115">[Omezení používání úrovní přístupu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): Souhrn omezení týkající se použití deklaraci úrovní přístupu.</span><span class="sxs-lookup"><span data-stu-id="fa1de-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1de-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa1de-116">See also</span></span>

- [<span data-ttu-id="fa1de-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fa1de-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="fa1de-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fa1de-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="fa1de-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fa1de-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="fa1de-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="fa1de-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="fa1de-121">Klíčová slova přístupu</span><span class="sxs-lookup"><span data-stu-id="fa1de-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)
- [<span data-ttu-id="fa1de-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="fa1de-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

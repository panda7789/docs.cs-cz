---
title: Přístup k modifikátory - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 587f1b03292db643d721e599ea93c39ba188117d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593016"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="81955-102">Modifikátory přístupu (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="81955-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="81955-103">Modifikátory přístupu jsou klíčová slova používaná k určení je deklarovaná přístupnost člena nebo typu.</span><span class="sxs-lookup"><span data-stu-id="81955-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="81955-104">Tato část představuje čtyři přístupu modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="81955-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="81955-105">Následujících šest úrovní přístupu se dá nastavit pomocí přístupu modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="81955-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="81955-106">[`public`](public.md): Přístup není omezený.</span><span class="sxs-lookup"><span data-stu-id="81955-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="81955-107">[`protected`](protected.md): Přístup je omezený na obsahující třídu nebo typy odvozené od třídy obsahující.</span><span class="sxs-lookup"><span data-stu-id="81955-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="81955-108">[`internal`](internal.md): Přístup je omezený na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="81955-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="81955-109">[`protected internal`](protected-internal.md): Přístup je omezený na aktuální sestavení nebo typy odvozené od třídy obsahující.</span><span class="sxs-lookup"><span data-stu-id="81955-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="81955-110">[`private`](private.md): Přístup je omezený na nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="81955-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="81955-111">[`private protected`](private-protected.md): Přístup je omezený na obsahující třídu nebo typy odvozené od třídy obsahující v rámci aktuálního sestavení.</span><span class="sxs-lookup"><span data-stu-id="81955-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="81955-112">Tato část představuje také následující:</span><span class="sxs-lookup"><span data-stu-id="81955-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="81955-113">[Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md): Chcete-li deklarovat šest úrovní usnadnění přístupu pomocí čtyř přístupu modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="81955-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="81955-114">[Doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md): Určuje, kde v částech programu může být odkazováno člena.</span><span class="sxs-lookup"><span data-stu-id="81955-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="81955-115">[Omezení používání úrovní přístupu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): Souhrn omezení týkající se použití deklaraci úrovní přístupu.</span><span class="sxs-lookup"><span data-stu-id="81955-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81955-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81955-116">See also</span></span>

- [<span data-ttu-id="81955-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="81955-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="81955-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="81955-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="81955-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="81955-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="81955-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="81955-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="81955-121">Klíčová slova přístupu</span><span class="sxs-lookup"><span data-stu-id="81955-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)
- [<span data-ttu-id="81955-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="81955-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

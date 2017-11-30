---
title: "Člen přetížení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b54a99ab88e4cfa0569b2095a0be3750c91f244
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="member-overloading"></a><span data-ttu-id="ad624-102">Člen přetížení</span><span class="sxs-lookup"><span data-stu-id="ad624-102">Member Overloading</span></span>
<span data-ttu-id="ad624-103">Člen přetížení znamená vytvoření dvou nebo více členů na stejný typ, který se liší pouze v číslo nebo typ parametry, ale mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="ad624-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="ad624-104">Například v následujícím příkladu `WriteLine` je přetížena metoda:</span><span class="sxs-lookup"><span data-stu-id="ad624-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="ad624-105">Protože parametry mohou obsahovat pouze metody, konstruktory a indexované vlastnosti, mohou být přetíženy pouze ty členy.</span><span class="sxs-lookup"><span data-stu-id="ad624-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="ad624-106">Přetížení je jedním z nejdůležitějších techniky pro zlepšení použitelnost, produktivity a čitelnost opakovaně použitelné knihovny.</span><span class="sxs-lookup"><span data-stu-id="ad624-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="ad624-107">Přetížení pro počet parametrů je možné poskytnout jednodušší verze konstruktorů a metod.</span><span class="sxs-lookup"><span data-stu-id="ad624-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="ad624-108">Přetížení na typ parametru umožňuje použít stejný název člena pro členy provádí na vybranou sadu různé typy stejné operace.</span><span class="sxs-lookup"><span data-stu-id="ad624-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="ad624-109">**PROVEĎTE ✓** zkuste použít parametr popisné názvy označíte, výchozí hodnotu použitou kratší přetíženími.</span><span class="sxs-lookup"><span data-stu-id="ad624-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="ad624-110">**X nepoužívejte** nahodile různými názvy parametrů v přetížení.</span><span class="sxs-lookup"><span data-stu-id="ad624-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="ad624-111">Pokud parametr v jedním přetížením představuje stejné vstupu jako parametr v jiné přetížení, parametry musí mít stejný název.</span><span class="sxs-lookup"><span data-stu-id="ad624-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="ad624-112">**X nepoužívejte** nekonzistentní v pořadí parametrů v přetížen členy.</span><span class="sxs-lookup"><span data-stu-id="ad624-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="ad624-113">Parametry se stejným názvem by se zobrazit ve stejné pozici v všechny přetížení.</span><span class="sxs-lookup"><span data-stu-id="ad624-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="ad624-114">**PROVEĎTE ✓** zkontrolujte virtuální pouze nejdelší přetížení (Pokud je vyžadována rozšíření).</span><span class="sxs-lookup"><span data-stu-id="ad624-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="ad624-115">Kratší přetížení by měly volat jednoduše prostřednictvím delší přetížení.</span><span class="sxs-lookup"><span data-stu-id="ad624-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="ad624-116">**X nesmí** použít `ref` nebo `out` modifikátory k přetížení členy.</span><span class="sxs-lookup"><span data-stu-id="ad624-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="ad624-117">Některé jazyky nelze vyřešit volání přetížení takto.</span><span class="sxs-lookup"><span data-stu-id="ad624-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="ad624-118">Kromě toho tyto přetížení obvykle mají úplně jiné sémantiku a pravděpodobně by neměla být přetížení ale dvě samostatné metody místo.</span><span class="sxs-lookup"><span data-stu-id="ad624-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="ad624-119">**X nesmí** , mají přetížení s parametry na stejné pozici a podobné typy, ale s jinou sémantiku.</span><span class="sxs-lookup"><span data-stu-id="ad624-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="ad624-120">**PROVEĎTE ✓** povolit `null` předávané volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="ad624-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="ad624-121">**PROVEĎTE ✓** použít člen přetížení než definování členy s výchozí argumenty.</span><span class="sxs-lookup"><span data-stu-id="ad624-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="ad624-122">Výchozí argumenty nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="ad624-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="ad624-123">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="ad624-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ad624-124">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="ad624-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad624-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad624-125">See Also</span></span>  
 [<span data-ttu-id="ad624-126">Člen pokynů pro návrh</span><span class="sxs-lookup"><span data-stu-id="ad624-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="ad624-127">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="ad624-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

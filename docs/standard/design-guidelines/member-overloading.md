---
title: Přetížení člena
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: KrzysztofCwalina
ms.openlocfilehash: 4caa0ae78d168b23fd2862153bef0e3960d3ea42
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392942"
---
# <a name="member-overloading"></a><span data-ttu-id="6baad-102">Přetížení člena</span><span class="sxs-lookup"><span data-stu-id="6baad-102">Member Overloading</span></span>
<span data-ttu-id="6baad-103">Přetížení členů znamená vytvoření dvou nebo více členů na stejném typu, které se liší pouze počtem nebo typem parametrů, ale mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="6baad-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="6baad-104">Například v následujícím příkladu je přetížená metoda `WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="6baad-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```csharp  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="6baad-105">Vzhledem k tomu, že pouze metody, konstruktory a indexované vlastnosti mohou mít parametry, mohou být přetíženy pouze tyto členy.</span><span class="sxs-lookup"><span data-stu-id="6baad-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="6baad-106">Přetížení je jedním z nejdůležitějších technik pro zlepšení použitelnosti, produktivity a čitelnosti opakovaně použitelných knihoven.</span><span class="sxs-lookup"><span data-stu-id="6baad-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="6baad-107">Přetížení na základě počtu parametrů umožňuje poskytovat jednodušší verze konstruktorů a metod.</span><span class="sxs-lookup"><span data-stu-id="6baad-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="6baad-108">Přetížení typu parametru umožňuje použít stejný název člena pro členy, kteří provádějí stejné operace na vybrané sadě různých typů.</span><span class="sxs-lookup"><span data-stu-id="6baad-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="6baad-109">**✓ DO** zkuste použít parametr popisné názvy označíte, výchozí hodnotu použitou kratší přetíženími.</span><span class="sxs-lookup"><span data-stu-id="6baad-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="6baad-110">**X AVOID** nahodile různými názvy parametrů v přetížení.</span><span class="sxs-lookup"><span data-stu-id="6baad-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="6baad-111">Pokud parametr v jednom přetížení představuje stejný vstup jako parametr v jiném přetížení, musí mít parametry stejný název.</span><span class="sxs-lookup"><span data-stu-id="6baad-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="6baad-112">**X AVOID** nekonzistentní v pořadí parametrů v přetížen členy.</span><span class="sxs-lookup"><span data-stu-id="6baad-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="6baad-113">Parametry se stejným názvem by měly být ve všech přetíženích ve stejné pozici.</span><span class="sxs-lookup"><span data-stu-id="6baad-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="6baad-114">**✓ DO** zkontrolujte virtuální pouze nejdelší přetížení (Pokud je vyžadována rozšíření).</span><span class="sxs-lookup"><span data-stu-id="6baad-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="6baad-115">Kratší přetížení by se měla jednoduše volat na delší přetížení.</span><span class="sxs-lookup"><span data-stu-id="6baad-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="6baad-116">**X DO NOT** použít `ref` nebo `out` modifikátory k přetížení členy.</span><span class="sxs-lookup"><span data-stu-id="6baad-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="6baad-117">Některé jazyky nemůžou vyřešit volání přetížení, jako je to.</span><span class="sxs-lookup"><span data-stu-id="6baad-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="6baad-118">Kromě toho taková přetížení obvykle mají zcela jinou sémantiku a pravděpodobně by neměla být přetížení, ale dvě samostatné metody.</span><span class="sxs-lookup"><span data-stu-id="6baad-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="6baad-119">**X DO NOT** , mají přetížení s parametry na stejné pozici a podobné typy, ale s jinou sémantiku.</span><span class="sxs-lookup"><span data-stu-id="6baad-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="6baad-120">**✓ DO** povolit `null` předávané volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="6baad-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="6baad-121">**✓ DO** použít člen přetížení než definování členy s výchozí argumenty.</span><span class="sxs-lookup"><span data-stu-id="6baad-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="6baad-122">Výchozí argumenty nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="6baad-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="6baad-123">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="6baad-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6baad-124">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="6baad-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6baad-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6baad-125">See also</span></span>

- [<span data-ttu-id="6baad-126">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="6baad-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="6baad-127">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="6baad-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

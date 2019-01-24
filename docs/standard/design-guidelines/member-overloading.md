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
ms.openlocfilehash: b13f9e1551aec7e53ba1ac2ed0b9049d46b0a756
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636648"
---
# <a name="member-overloading"></a><span data-ttu-id="a4efc-102">Přetížení člena</span><span class="sxs-lookup"><span data-stu-id="a4efc-102">Member Overloading</span></span>
<span data-ttu-id="a4efc-103">Přetížení člena znamená, že vytvoření dvou nebo více členů na stejný typ, který se liší pouze velikostí číslo nebo typ parametrů, ale mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="a4efc-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="a4efc-104">Například v následujícím příkladu `WriteLine` přetížené metody:</span><span class="sxs-lookup"><span data-stu-id="a4efc-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="a4efc-105">Protože pouze metody, konstruktory a indexované vlastnosti mohou mít parametry, mohou být přetíženy pouze ty členy.</span><span class="sxs-lookup"><span data-stu-id="a4efc-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="a4efc-106">Přetěžování je jedním z nejdůležitějších technik pro vylepšení použitelnosti, produktivitu a čitelnost opakovaně použitelné knihovny.</span><span class="sxs-lookup"><span data-stu-id="a4efc-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="a4efc-107">Přetížení pro počet parametrů umožňuje poskytují jednodušší verze konstruktorů a metod.</span><span class="sxs-lookup"><span data-stu-id="a4efc-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="a4efc-108">Přetížení u parametru typu umožňuje použití stejného názvu členu pro provádění operací identické na vybrané sadě různé typy členů.</span><span class="sxs-lookup"><span data-stu-id="a4efc-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="a4efc-109">**✓ DO** zkuste použít parametr popisné názvy označíte, výchozí hodnotu použitou kratší přetíženími.</span><span class="sxs-lookup"><span data-stu-id="a4efc-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="a4efc-110">**X AVOID** nahodile různými názvy parametrů v přetížení.</span><span class="sxs-lookup"><span data-stu-id="a4efc-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="a4efc-111">Pokud parametr v jedním přetížením představuje stejný vstup jako parametr v jiné přetížení, parametry, by měly být stejné.</span><span class="sxs-lookup"><span data-stu-id="a4efc-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="a4efc-112">**X AVOID** nekonzistentní v pořadí parametrů v přetížen členy.</span><span class="sxs-lookup"><span data-stu-id="a4efc-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="a4efc-113">Parametry se stejným názvem, by se zobrazit na stejné pozici v všechna přetížení.</span><span class="sxs-lookup"><span data-stu-id="a4efc-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="a4efc-114">**✓ DO** zkontrolujte virtuální pouze nejdelší přetížení (Pokud je vyžadována rozšíření).</span><span class="sxs-lookup"><span data-stu-id="a4efc-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="a4efc-115">Kratší přetížení by měly volat pouze prostřednictvím delší přetížení.</span><span class="sxs-lookup"><span data-stu-id="a4efc-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="a4efc-116">**X DO NOT** použít `ref` nebo `out` modifikátory k přetížení členy.</span><span class="sxs-lookup"><span data-stu-id="a4efc-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="a4efc-117">Některé jazyky nejde vyřešit volání přetížení následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="a4efc-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="a4efc-118">Kromě toho takovými přetíženími obvykle mít úplně odlišnou sémantiku a pravděpodobně by neměl být přetížení, ale dvě samostatné metody místo.</span><span class="sxs-lookup"><span data-stu-id="a4efc-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="a4efc-119">**X DO NOT** , mají přetížení s parametry na stejné pozici a podobné typy, ale s jinou sémantiku.</span><span class="sxs-lookup"><span data-stu-id="a4efc-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="a4efc-120">**✓ DO** povolit `null` předávané volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="a4efc-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="a4efc-121">**✓ DO** použít člen přetížení než definování členy s výchozí argumenty.</span><span class="sxs-lookup"><span data-stu-id="a4efc-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="a4efc-122">Výchozí argumenty nejsou kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="a4efc-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="a4efc-123">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="a4efc-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a4efc-124">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="a4efc-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4efc-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4efc-125">See also</span></span>

- [<span data-ttu-id="a4efc-126">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="a4efc-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="a4efc-127">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="a4efc-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

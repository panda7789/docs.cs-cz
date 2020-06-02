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
ms.openlocfilehash: 6a2cd6d4dd293a7f4a408e1ee97a125c9454be41
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289002"
---
# <a name="member-overloading"></a><span data-ttu-id="52e61-102">Přetížení člena</span><span class="sxs-lookup"><span data-stu-id="52e61-102">Member Overloading</span></span>
<span data-ttu-id="52e61-103">Přetížení členů znamená vytvoření dvou nebo více členů na stejném typu, které se liší pouze počtem nebo typem parametrů, ale mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="52e61-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="52e61-104">Například v následujícím příkladu `WriteLine` je metoda přetížena:</span><span class="sxs-lookup"><span data-stu-id="52e61-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 <span data-ttu-id="52e61-105">Vzhledem k tomu, že pouze metody, konstruktory a indexované vlastnosti mohou mít parametry, mohou být přetíženy pouze tyto členy.</span><span class="sxs-lookup"><span data-stu-id="52e61-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>

 <span data-ttu-id="52e61-106">Přetížení je jedním z nejdůležitějších technik pro zlepšení použitelnosti, produktivity a čitelnosti opakovaně použitelných knihoven.</span><span class="sxs-lookup"><span data-stu-id="52e61-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="52e61-107">Přetížení na základě počtu parametrů umožňuje poskytovat jednodušší verze konstruktorů a metod.</span><span class="sxs-lookup"><span data-stu-id="52e61-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="52e61-108">Přetížení typu parametru umožňuje použít stejný název člena pro členy, kteří provádějí stejné operace na vybrané sadě různých typů.</span><span class="sxs-lookup"><span data-stu-id="52e61-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>

 <span data-ttu-id="52e61-109">✔️ se pokuste použít názvy popisných parametrů k označení výchozí hodnoty používané kratšími přetíženími.</span><span class="sxs-lookup"><span data-stu-id="52e61-109">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>

 <span data-ttu-id="52e61-110">❌Vyhněte se svévolnému proměnlivosti názvů parametrů v přetíženích.</span><span class="sxs-lookup"><span data-stu-id="52e61-110">❌ AVOID arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="52e61-111">Pokud parametr v jednom přetížení představuje stejný vstup jako parametr v jiném přetížení, musí mít parametry stejný název.</span><span class="sxs-lookup"><span data-stu-id="52e61-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>

 <span data-ttu-id="52e61-112">❌Vyhněte se nekonzistenci v pořadí parametrů v přetížených členech.</span><span class="sxs-lookup"><span data-stu-id="52e61-112">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="52e61-113">Parametry se stejným názvem by měly být ve všech přetíženích ve stejné pozici.</span><span class="sxs-lookup"><span data-stu-id="52e61-113">Parameters with the same name should appear in the same position in all overloads.</span></span>

 <span data-ttu-id="52e61-114">✔️ UDĚLAT jenom nejdelší přetížený virtuální (Pokud se vyžaduje rozšiřitelnost).</span><span class="sxs-lookup"><span data-stu-id="52e61-114">✔️ DO make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="52e61-115">Kratší přetížení by se měla jednoduše volat na delší přetížení.</span><span class="sxs-lookup"><span data-stu-id="52e61-115">Shorter overloads should simply call through to a longer overload.</span></span>

 <span data-ttu-id="52e61-116">❌Nepoužívejte `ref` ani `out` modifikátory k přetížení členů.</span><span class="sxs-lookup"><span data-stu-id="52e61-116">❌ DO NOT use `ref` or `out` modifiers to overload members.</span></span>

 <span data-ttu-id="52e61-117">Některé jazyky nemůžou vyřešit volání přetížení, jako je to.</span><span class="sxs-lookup"><span data-stu-id="52e61-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="52e61-118">Kromě toho taková přetížení obvykle mají zcela jinou sémantiku a pravděpodobně by neměla být přetížení, ale dvě samostatné metody.</span><span class="sxs-lookup"><span data-stu-id="52e61-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>

 <span data-ttu-id="52e61-119">❌Nepoužívejte přetížení s parametry na stejné pozici a podobných typech ještě s různou sémantikou.</span><span class="sxs-lookup"><span data-stu-id="52e61-119">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span></span>

 <span data-ttu-id="52e61-120">✔️ je možné `null` předat pro volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="52e61-120">✔️ DO  allow `null` to be passed for optional arguments.</span></span>

 <span data-ttu-id="52e61-121">✔️ použít přetížení členů namísto definování členů s výchozími argumenty.</span><span class="sxs-lookup"><span data-stu-id="52e61-121">✔️ DO use member overloading rather than defining members with default arguments.</span></span>

 <span data-ttu-id="52e61-122">Výchozí argumenty nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="52e61-122">Default arguments are not CLS compliant.</span></span>

 <span data-ttu-id="52e61-123">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="52e61-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="52e61-124">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="52e61-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="52e61-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="52e61-125">See also</span></span>

- [<span data-ttu-id="52e61-126">Pokyny pro návrh členů</span><span class="sxs-lookup"><span data-stu-id="52e61-126">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="52e61-127">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="52e61-127">Framework Design Guidelines</span></span>](index.md)

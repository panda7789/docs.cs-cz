---
title: Návrh struktury
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: c6ac53014e048da3a90dd7b8e961176f61e90355
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290808"
---
# <a name="struct-design"></a><span data-ttu-id="64cab-102">Návrh struktury</span><span class="sxs-lookup"><span data-stu-id="64cab-102">Struct Design</span></span>
<span data-ttu-id="64cab-103">Typ hodnoty pro obecné účely se nejčastěji označuje jako struktura, její klíčové slovo jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="64cab-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="64cab-104">V této části najdete pokyny pro obecný návrh struktury.</span><span class="sxs-lookup"><span data-stu-id="64cab-104">This section provides guidelines for general struct design.</span></span>

 <span data-ttu-id="64cab-105">❌Neposkytněte konstruktor bez parametrů pro strukturu.</span><span class="sxs-lookup"><span data-stu-id="64cab-105">❌ DO NOT provide a parameterless constructor for a struct.</span></span>

 <span data-ttu-id="64cab-106">Podle těchto pokynů umožňuje vytvořit pole struktur bez nutnosti spuštění konstruktoru pro každou položku pole.</span><span class="sxs-lookup"><span data-stu-id="64cab-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="64cab-107">Všimněte si, že jazyk C# neumožňuje strukturám konstruktory bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="64cab-107">Notice that C# does not allow structs to have parameterless constructors.</span></span>

 <span data-ttu-id="64cab-108">❌Nedefinujte proměnlivé hodnoty typů.</span><span class="sxs-lookup"><span data-stu-id="64cab-108">❌ DO NOT define mutable value types.</span></span>

 <span data-ttu-id="64cab-109">Proměnlivé typy hodnot mají několik problémů.</span><span class="sxs-lookup"><span data-stu-id="64cab-109">Mutable value types have several problems.</span></span> <span data-ttu-id="64cab-110">Například pokud vlastnost getter vrátí typ hodnoty, volající obdrží kopii.</span><span class="sxs-lookup"><span data-stu-id="64cab-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="64cab-111">Vzhledem k tomu, že kopie je vytvořena implicitně, vývojáři nemusí vědět, že se jedná o kopii, a nikoli původní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="64cab-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="64cab-112">Také některé jazyky (například dynamické jazyky) mají problémy s použitím proměnlivých hodnotových typů, protože i místní proměnné, pokud jsou převedené, způsobují vytvoření kopie.</span><span class="sxs-lookup"><span data-stu-id="64cab-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>

 <span data-ttu-id="64cab-113">✔️ Zajistěte, aby byl stav, kde jsou všechna data instance nastavena na hodnotu nula, false nebo null (podle potřeby).</span><span class="sxs-lookup"><span data-stu-id="64cab-113">✔️ DO ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>

 <span data-ttu-id="64cab-114">To brání nechtěnému vytvoření neplatných instancí při vytvoření pole struktury.</span><span class="sxs-lookup"><span data-stu-id="64cab-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>

 <span data-ttu-id="64cab-115">✔️ PROVÉST implementaci <xref:System.IEquatable%601> na typech hodnot.</span><span class="sxs-lookup"><span data-stu-id="64cab-115">✔️ DO implement <xref:System.IEquatable%601> on value types.</span></span>

 <span data-ttu-id="64cab-116"><xref:System.Object.Equals%2A?displayProperty=nameWithType>Metoda na hodnotových typech způsobuje zabalení a její výchozí implementace není velmi efektivní, protože používá reflexi.</span><span class="sxs-lookup"><span data-stu-id="64cab-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="64cab-117"><xref:System.IEquatable%601.Equals%2A>může mít mnohem lepší výkon a může být implementováno tak, že nebude způsobovat zabalení.</span><span class="sxs-lookup"><span data-stu-id="64cab-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>

 <span data-ttu-id="64cab-118">❌Nepoužívejte explicitně <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="64cab-118">❌ DO NOT explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="64cab-119">Většinou tyto jazyky tuto skutečnost znemožňují.</span><span class="sxs-lookup"><span data-stu-id="64cab-119">In fact, most languages prevent this.</span></span>

 <span data-ttu-id="64cab-120">Obecně mohou být struktury velmi užitečné, ale měly by být použity pouze pro malé, jednoduché, neměnné hodnoty, které nebudou často zabaleny.</span><span class="sxs-lookup"><span data-stu-id="64cab-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>

 <span data-ttu-id="64cab-121">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="64cab-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="64cab-122">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="64cab-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="64cab-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="64cab-123">See also</span></span>

- [<span data-ttu-id="64cab-124">Pokyny pro návrh typů</span><span class="sxs-lookup"><span data-stu-id="64cab-124">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="64cab-125">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="64cab-125">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="64cab-126">Volba mezi třídou a strukturou</span><span class="sxs-lookup"><span data-stu-id="64cab-126">Choosing Between Class and Struct</span></span>](choosing-between-class-and-struct.md)

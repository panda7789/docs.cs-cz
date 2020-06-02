---
title: Návrh rozhraní
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: f589d47d5b945179430275598996b2fb77e92848
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289028"
---
# <a name="interface-design"></a><span data-ttu-id="22fa4-102">Návrh rozhraní</span><span class="sxs-lookup"><span data-stu-id="22fa4-102">Interface Design</span></span>
<span data-ttu-id="22fa4-103">I když je většina rozhraní API nejlépe modelována pomocí tříd a struktur, existují případy, kdy jsou rozhraní lépe vhodná, nebo jenom možnost.</span><span class="sxs-lookup"><span data-stu-id="22fa4-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>

 <span data-ttu-id="22fa4-104">CLR nepodporuje vícenásobnou dědičnost (tj. třídy CLR nemůžou dědit z více než jedné základní třídy), ale umožňuje typům implementovat jednu nebo více rozhraní kromě dědění ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="22fa4-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="22fa4-105">Rozhraní se proto často používají k dosažení účinku vícenásobné dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="22fa4-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="22fa4-106">Například <xref:System.IDisposable> je rozhraní, které umožňuje typům podporovat disposability nezávisle na jakékoli jiné hierarchii dědičnosti, v níž se chtějí zúčastnit.</span><span class="sxs-lookup"><span data-stu-id="22fa4-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>

 <span data-ttu-id="22fa4-107">Další situací, ve které je definování rozhraní vhodné, je vytvoření společného rozhraní, které může být podporováno několika typy, včetně některých typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="22fa4-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="22fa4-108">Typy hodnot nemůžou dědit z jiných typů než <xref:System.ValueType> , ale můžou implementovat rozhraní, takže použití rozhraní je jedinou možností, aby se mohl poskytnout společný základní typ.</span><span class="sxs-lookup"><span data-stu-id="22fa4-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>

 <span data-ttu-id="22fa4-109">✔️ definovat rozhraní, pokud potřebujete některé společné rozhraní API podporovat sadou typů, které obsahují typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="22fa4-109">✔️ DO define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>

 <span data-ttu-id="22fa4-110">✔️ Zvažte definování rozhraní, pokud potřebujete podporovat jeho funkci u typů, které již dědí z jiného typu.</span><span class="sxs-lookup"><span data-stu-id="22fa4-110">✔️ CONSIDER defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>

 <span data-ttu-id="22fa4-111">❌Vyhněte se použití rozhraní značek (rozhraní bez členů).</span><span class="sxs-lookup"><span data-stu-id="22fa4-111">❌ AVOID using marker interfaces (interfaces with no members).</span></span>

 <span data-ttu-id="22fa4-112">Pokud potřebujete označit třídu jako se specifickou charakteristikou (marker), použijte obecně vlastní atribut, nikoli rozhraní.</span><span class="sxs-lookup"><span data-stu-id="22fa4-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>

 <span data-ttu-id="22fa4-113">✔️ Zadejte alespoň jeden typ, který je implementací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="22fa4-113">✔️ DO provide at least one type that is an implementation of an interface.</span></span>

 <span data-ttu-id="22fa4-114">To pomáhá ověřit návrh rozhraní.</span><span class="sxs-lookup"><span data-stu-id="22fa4-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="22fa4-115">Například <xref:System.Collections.Generic.List%601> je implementací <xref:System.Collections.Generic.IList%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="22fa4-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>

 <span data-ttu-id="22fa4-116">✔️ Zadejte alespoň jedno rozhraní API, které využívá každé rozhraní, které definujete (metodu přebírající rozhraní jako parametr nebo vlastnost typu jako rozhraní).</span><span class="sxs-lookup"><span data-stu-id="22fa4-116">✔️ DO provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>

 <span data-ttu-id="22fa4-117">To pomáhá ověřit návrh rozhraní.</span><span class="sxs-lookup"><span data-stu-id="22fa4-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="22fa4-118">Například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> používá <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="22fa4-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>

 <span data-ttu-id="22fa4-119">❌Nepřidávat členy do rozhraní, které bylo dříve expedováno.</span><span class="sxs-lookup"><span data-stu-id="22fa4-119">❌ DO NOT add members to an interface that has previously shipped.</span></span>

 <span data-ttu-id="22fa4-120">Tím by došlo k přerušení implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="22fa4-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="22fa4-121">Aby nedocházelo k problémům se správou verzí, měli byste vytvořit nové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="22fa4-121">You should create a new interface in order to avoid versioning problems.</span></span>

 <span data-ttu-id="22fa4-122">S výjimkou případů popsaných v těchto pokynech byste měli obecně zvolit třídy namísto rozhraní v návrhu opakovaně použitelných knihoven spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="22fa4-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>

 <span data-ttu-id="22fa4-123">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="22fa4-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="22fa4-124">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="22fa4-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="22fa4-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="22fa4-125">See also</span></span>

- [<span data-ttu-id="22fa4-126">Pokyny pro návrh typů</span><span class="sxs-lookup"><span data-stu-id="22fa4-126">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="22fa4-127">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="22fa4-127">Framework Design Guidelines</span></span>](index.md)

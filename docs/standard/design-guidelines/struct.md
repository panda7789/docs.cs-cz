---
title: "Struktura návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1566d2b67e1dda5b0b221a2c10affb6bdaea888
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="struct-design"></a><span data-ttu-id="acd8a-102">Struktura návrhu</span><span class="sxs-lookup"><span data-stu-id="acd8a-102">Struct Design</span></span>
<span data-ttu-id="acd8a-103">Typ hodnoty pro obecné účely se nejčastěji označuje jako struktury, jeho C# – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="acd8a-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="acd8a-104">Tato část obsahuje pokyny pro návrh obecná struktura.</span><span class="sxs-lookup"><span data-stu-id="acd8a-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="acd8a-105">**X nesmí** zadejte výchozí konstruktor pro struktury.</span><span class="sxs-lookup"><span data-stu-id="acd8a-105">**X DO NOT** provide a default constructor for a struct.</span></span>  
  
 <span data-ttu-id="acd8a-106">Následující obecné této zásady umožňuje pole struktur, který se má vytvořit bez nutnosti spuštění konstruktoru na každou položku pole.</span><span class="sxs-lookup"><span data-stu-id="acd8a-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="acd8a-107">Všimněte si, že C# neumožňuje struktury tak, aby měl výchozí konstruktory.</span><span class="sxs-lookup"><span data-stu-id="acd8a-107">Notice that C# does not allow structs to have default constructors.</span></span>  
  
 <span data-ttu-id="acd8a-108">**X nesmí** definování typů měnitelný hodnotu.</span><span class="sxs-lookup"><span data-stu-id="acd8a-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="acd8a-109">Typy hodnot měnitelný mít několik problémů.</span><span class="sxs-lookup"><span data-stu-id="acd8a-109">Mutable value types have several problems.</span></span> <span data-ttu-id="acd8a-110">Například v případě, že metoda getter vlastnosti vrátí typ hodnoty, volající obdrží kopii.</span><span class="sxs-lookup"><span data-stu-id="acd8a-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="acd8a-111">Protože kopie je vytvořena implicitně, nemusíte být vědomi, mutace kopií a není původní hodnota vývojáři.</span><span class="sxs-lookup"><span data-stu-id="acd8a-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="acd8a-112">Některé jazyky (dynamické jazyky konkrétně) také mít problémy pomocí typy měnitelný hodnot, protože dokonce i místní proměnné, když vyhodnoceny odkazy, způsobit kopie má být provedeno.</span><span class="sxs-lookup"><span data-stu-id="acd8a-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="acd8a-113">**PROVEĎTE ✓** jistotu, že stav, kde všechny instance dat je nastavený na nulu, false, nebo hodnotu null (podle potřeby) je platný.</span><span class="sxs-lookup"><span data-stu-id="acd8a-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="acd8a-114">Při vytváření pole struktury zabrání náhodnému vytváření instancí neplatný.</span><span class="sxs-lookup"><span data-stu-id="acd8a-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="acd8a-115">**PROVEĎTE ✓** implementovat <xref:System.IEquatable%601> u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="acd8a-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="acd8a-116"><xref:System.Object.Equals%2A?displayProperty=nameWithType> Metoda u typů hodnot způsobí, že zabalení a jeho výchozí implementace není velmi efektivní, protože používá reflexe.</span><span class="sxs-lookup"><span data-stu-id="acd8a-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="acd8a-117"><xref:System.IEquatable%601.Equals%2A>může mít mnohem lepší výkon a může být implementováno tak, aby nezpůsobí zabalení.</span><span class="sxs-lookup"><span data-stu-id="acd8a-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="acd8a-118">**X nesmí** explicitně rozšířit <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="acd8a-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="acd8a-119">Většina jazyků zabránit ve skutečnosti to.</span><span class="sxs-lookup"><span data-stu-id="acd8a-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="acd8a-120">Obecně platí struktury může být velmi užitečná, ale musí být použit pouze pro malé, jeden, neměnné hodnoty, které nebudou často do pole.</span><span class="sxs-lookup"><span data-stu-id="acd8a-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="acd8a-121">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="acd8a-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="acd8a-122">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="acd8a-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd8a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="acd8a-123">See Also</span></span>  
 [<span data-ttu-id="acd8a-124">Typ pokynů pro návrh</span><span class="sxs-lookup"><span data-stu-id="acd8a-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="acd8a-125">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="acd8a-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="acd8a-126">Volba mezi třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="acd8a-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)

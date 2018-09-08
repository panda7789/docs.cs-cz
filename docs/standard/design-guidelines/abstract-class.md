---
title: Návrh abstraktní třídy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5b9dacc4995a126e1ee3f6062dca796194d4882
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128521"
---
# <a name="abstract-class-design"></a><span data-ttu-id="72c5b-102">Návrh abstraktní třídy</span><span class="sxs-lookup"><span data-stu-id="72c5b-102">Abstract Class Design</span></span>
<span data-ttu-id="72c5b-103">**X DO NOT** definice veřejných nebo chráněného interní konstruktorů v abstraktních typech.</span><span class="sxs-lookup"><span data-stu-id="72c5b-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="72c5b-104">Konstruktory by měly být veřejné, pouze v případě, že uživatelé budou potřebovat k vytvoření instance daného typu.</span><span class="sxs-lookup"><span data-stu-id="72c5b-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="72c5b-105">Protože nelze vytvořit instance abstraktního typu, abstraktní typ s veřejným konstruktorem je nesprávně navrženy a pro uživatele matoucí.</span><span class="sxs-lookup"><span data-stu-id="72c5b-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="72c5b-106">**✓ DO** definice s chráněným nebo interní konstruktor v abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="72c5b-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="72c5b-107">Chráněný konstruktor je běžné a jednoduše umožňuje udělat vlastní inicializaci, když jsou vytvořeny podtypy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="72c5b-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="72c5b-108">Interní konstruktor slouží k omezení konkrétní implementace abstraktní třídu pro sestavení, definice třídy.</span><span class="sxs-lookup"><span data-stu-id="72c5b-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="72c5b-109">**✓ DO** zadejte alespoň jeden konkrétní typ, který dědí z každé abstraktní třída, která můžete dodávat.</span><span class="sxs-lookup"><span data-stu-id="72c5b-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="72c5b-110">Provádí se to pomáhá k ověření návrh abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="72c5b-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="72c5b-111">Například <xref:System.IO.FileStream?displayProperty=nameWithType> je implementace <xref:System.IO.Stream?displayProperty=nameWithType> abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="72c5b-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="72c5b-112">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="72c5b-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="72c5b-113">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="72c5b-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c5b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72c5b-114">See also</span></span>

- [<span data-ttu-id="72c5b-115">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="72c5b-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="72c5b-116">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="72c5b-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

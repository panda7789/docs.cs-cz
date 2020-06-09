---
title: Parametry pojmenování
description: Přečtěte si pokyny pro pojmenovávání parametrů. Například použijte popisné názvy parametrů & ve stylu CamelCase velikosti písmen, & zvažte pojmenování na základě významu místo typu.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 54f37c4d6a0f9a6931fa69d612bf0e45bf1f2ce7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583515"
---
# <a name="naming-parameters"></a><span data-ttu-id="61c2a-104">Parametry pojmenování</span><span class="sxs-lookup"><span data-stu-id="61c2a-104">Naming Parameters</span></span>
<span data-ttu-id="61c2a-105">Kromě zjevného důvodu čitelnosti je důležité postupovat podle pokynů pro názvy parametrů, protože parametry jsou zobrazeny v dokumentaci a v návrháři, když nástroje vizuálního návrhu poskytují funkce IntelliSense a procházení tříd.</span><span class="sxs-lookup"><span data-stu-id="61c2a-105">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="61c2a-106">✔️ použít camelCasing v názvech parametrů.</span><span class="sxs-lookup"><span data-stu-id="61c2a-106">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="61c2a-107">✔️ použít popisné názvy parametrů.</span><span class="sxs-lookup"><span data-stu-id="61c2a-107">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="61c2a-108">✔️ Zvažte použití názvů založených na významu parametru, nikoli typu parametru.</span><span class="sxs-lookup"><span data-stu-id="61c2a-108">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="61c2a-109">Parametry přetížení operátoru názvů</span><span class="sxs-lookup"><span data-stu-id="61c2a-109">Naming Operator Overload Parameters</span></span>
 <span data-ttu-id="61c2a-110">✔️ použít `left` a `right` pro přetížení binárního operátoru názvy parametrů, pokud neexistuje význam pro parametry.</span><span class="sxs-lookup"><span data-stu-id="61c2a-110">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="61c2a-111">✔️ použít `value` pro názvy parametrů přetížení unárního operátoru, pokud neexistuje význam parametrů.</span><span class="sxs-lookup"><span data-stu-id="61c2a-111">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="61c2a-112">Pokud to uděláte, ✔️ zvažte smysluplné názvy parametrů přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="61c2a-112">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="61c2a-113">❌Nepoužívejte zkratky ani číselné indexy pro názvy parametrů přetížení operátorů.</span><span class="sxs-lookup"><span data-stu-id="61c2a-113">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="61c2a-114">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="61c2a-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="61c2a-115">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="61c2a-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="61c2a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="61c2a-116">See also</span></span>

- [<span data-ttu-id="61c2a-117">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="61c2a-117">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="61c2a-118">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="61c2a-118">Naming Guidelines</span></span>](naming-guidelines.md)

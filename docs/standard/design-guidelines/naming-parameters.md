---
title: Parametry pojmenování
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: ebe2e2db4b109057bf576d4e18cfe511c657707e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743827"
---
# <a name="naming-parameters"></a><span data-ttu-id="ebb59-102">Parametry pojmenování</span><span class="sxs-lookup"><span data-stu-id="ebb59-102">Naming Parameters</span></span>
<span data-ttu-id="ebb59-103">Kromě zjevného důvodu čitelnosti je důležité postupovat podle pokynů pro názvy parametrů, protože parametry jsou zobrazeny v dokumentaci a v návrháři, když nástroje vizuálního návrhu poskytují funkce IntelliSense a procházení tříd.</span><span class="sxs-lookup"><span data-stu-id="ebb59-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="ebb59-104">✔️ použít camelCasing v názvech parametrů.</span><span class="sxs-lookup"><span data-stu-id="ebb59-104">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="ebb59-105">✔️ použít popisné názvy parametrů.</span><span class="sxs-lookup"><span data-stu-id="ebb59-105">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="ebb59-106">✔️ Zvažte použití názvů založených na významu parametru, nikoli typu parametru.</span><span class="sxs-lookup"><span data-stu-id="ebb59-106">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="ebb59-107">Parametry přetížení operátoru názvů</span><span class="sxs-lookup"><span data-stu-id="ebb59-107">Naming Operator Overload Parameters</span></span>
 <span data-ttu-id="ebb59-108">✔️ použít `left` a `right` pro názvy parametrů přetížení binárního operátoru, pokud neexistuje význam pro parametry.</span><span class="sxs-lookup"><span data-stu-id="ebb59-108">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="ebb59-109">✔️ použít `value` pro názvy parametrů přetížení unárních operátorů, pokud neexistuje význam parametrů.</span><span class="sxs-lookup"><span data-stu-id="ebb59-109">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="ebb59-110">Pokud to uděláte, ✔️ zvažte smysluplné názvy parametrů přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="ebb59-110">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="ebb59-111">❌ Nepoužívejte zkratky ani číselné indexy pro názvy parametrů přetížení operátorů.</span><span class="sxs-lookup"><span data-stu-id="ebb59-111">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="ebb59-112">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="ebb59-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ebb59-113">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="ebb59-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ebb59-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebb59-114">See also</span></span>

- [<span data-ttu-id="ebb59-115">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="ebb59-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ebb59-116">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="ebb59-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

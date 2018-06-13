---
title: Názvy parametrů
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed6b96bb05c52de4bfd8b6ad6b972c9d22ca66da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570483"
---
# <a name="naming-parameters"></a><span data-ttu-id="04f27-102">Názvy parametrů</span><span class="sxs-lookup"><span data-stu-id="04f27-102">Naming Parameters</span></span>
<span data-ttu-id="04f27-103">Nad rámec zřejmé čitelnosti důvod, proč je důležité postupujte podle pokynů pro názvy parametrů, protože parametry jsou zobrazeny v dokumentaci a v návrháři, když nástrojů visual návrhu poskytují Intellisense a třída procházení funkce.</span><span class="sxs-lookup"><span data-stu-id="04f27-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="04f27-104">**PROVEĎTE ✓** použít camelCasing v názvech parametrů.</span><span class="sxs-lookup"><span data-stu-id="04f27-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="04f27-105">**PROVEĎTE ✓** použít parametr popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="04f27-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="04f27-106">**✓ ZVAŽTE** pomocí názvů založených na parametr význam, nikoli typ parametru.</span><span class="sxs-lookup"><span data-stu-id="04f27-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="04f27-107">Názvy parametrů přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="04f27-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="04f27-108">**PROVEĎTE ✓** použít `left` a `right` pro názvy parametrů přetížení binární operátor Pokud neexistuje žádný význam na parametry.</span><span class="sxs-lookup"><span data-stu-id="04f27-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="04f27-109">**PROVEĎTE ✓** použít `value` pro unární operátor přetížení názvy parametrů, pokud neexistuje žádný význam na parametry.</span><span class="sxs-lookup"><span data-stu-id="04f27-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="04f27-110">**✓ ZVAŽTE** smysluplný názvy pro operátor přetížení parametry, pokud tento postup zvětší významné zlepšení.</span><span class="sxs-lookup"><span data-stu-id="04f27-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="04f27-111">**X nesmí** používání zkratky nebo číselné indexů pro operátor přetížení názvy parametrů.</span><span class="sxs-lookup"><span data-stu-id="04f27-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="04f27-112">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="04f27-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="04f27-113">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="04f27-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f27-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="04f27-114">See Also</span></span>  
 [<span data-ttu-id="04f27-115">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="04f27-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="04f27-116">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="04f27-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

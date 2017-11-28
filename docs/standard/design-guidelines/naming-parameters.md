---
title: "Názvy parametrů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b61f2b56b3b8bab67cec6db68a76916c6d7fa05a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="naming-parameters"></a><span data-ttu-id="0eaaf-102">Názvy parametrů</span><span class="sxs-lookup"><span data-stu-id="0eaaf-102">Naming Parameters</span></span>
<span data-ttu-id="0eaaf-103">Nad rámec zřejmé čitelnosti důvod, proč je důležité postupujte podle pokynů pro názvy parametrů, protože parametry jsou zobrazeny v dokumentaci a v návrháři, když nástrojů visual návrhu poskytují Intellisense a třída procházení funkce.</span><span class="sxs-lookup"><span data-stu-id="0eaaf-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="0eaaf-104">**PROVEĎTE ✓** použít camelCasing v názvech parametrů.</span><span class="sxs-lookup"><span data-stu-id="0eaaf-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="0eaaf-105">**PROVEĎTE ✓** použít parametr popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="0eaaf-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="0eaaf-106">**✓ ZVAŽTE** pomocí názvů založených na parametr význam, nikoli typ parametru.</span><span class="sxs-lookup"><span data-stu-id="0eaaf-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="0eaaf-107">Názvy parametrů přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="0eaaf-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="0eaaf-108">**PROVEĎTE ✓** použít `left` a `right` pro názvy parametrů přetížení binární operátor Pokud neexistuje žádný význam na parametry.</span><span class="sxs-lookup"><span data-stu-id="0eaaf-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="0eaaf-109">**PROVEĎTE ✓** použít `value` pro unární operátor přetížení názvy parametrů, pokud neexistuje žádný význam na parametry.</span><span class="sxs-lookup"><span data-stu-id="0eaaf-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="0eaaf-110">**✓ ZVAŽTE** smysluplný názvy pro operátor přetížení parametry, pokud tento postup zvětší významné zlepšení.</span><span class="sxs-lookup"><span data-stu-id="0eaaf-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="0eaaf-111">**X nesmí** používání zkratky nebo číselné indexů pro operátor přetížení názvy parametrů.</span><span class="sxs-lookup"><span data-stu-id="0eaaf-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="0eaaf-112">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="0eaaf-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0eaaf-113">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="0eaaf-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eaaf-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="0eaaf-114">See Also</span></span>  
 [<span data-ttu-id="0eaaf-115">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="0eaaf-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="0eaaf-116">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="0eaaf-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

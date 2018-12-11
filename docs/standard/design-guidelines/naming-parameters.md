---
title: Parametry pojmenování
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: KrzysztofCwalina
ms.openlocfilehash: 35965f03f5c50cbe3ffcc9bdb615d99c50fc30a2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147908"
---
# <a name="naming-parameters"></a><span data-ttu-id="80749-102">Parametry pojmenování</span><span class="sxs-lookup"><span data-stu-id="80749-102">Naming Parameters</span></span>
<span data-ttu-id="80749-103">Nad rámec zřejmé z důvodu čitelnosti je potřeba postupovat podle pokynů pro názvy parametrů, protože parametry jsou zobrazeny v dokumentaci a v návrháři, když poskytují vizuální návrh nástroje technologie Intellisense a procházení funkce třídy.</span><span class="sxs-lookup"><span data-stu-id="80749-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="80749-104">**✓ DO** použít camelCasing v názvech parametrů.</span><span class="sxs-lookup"><span data-stu-id="80749-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="80749-105">**✓ DO** použít parametr popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="80749-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="80749-106">**✓ CONSIDER** pomocí názvů založených na parametr význam, nikoli typ parametru.</span><span class="sxs-lookup"><span data-stu-id="80749-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="80749-107">Pojmenovávání parametrů přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="80749-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="80749-108">**✓ DO** použít `left` a `right` pro názvy parametrů přetížení binární operátor Pokud neexistuje žádný význam na parametry.</span><span class="sxs-lookup"><span data-stu-id="80749-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="80749-109">**✓ DO** použít `value` pro unární operátor přetížení názvy parametrů, pokud neexistuje žádný význam na parametry.</span><span class="sxs-lookup"><span data-stu-id="80749-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="80749-110">**✓ CONSIDER** smysluplný názvy pro operátor přetížení parametry, pokud tento postup zvětší významné zlepšení.</span><span class="sxs-lookup"><span data-stu-id="80749-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="80749-111">**X DO NOT** používání zkratky nebo číselné indexů pro operátor přetížení názvy parametrů.</span><span class="sxs-lookup"><span data-stu-id="80749-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="80749-112">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="80749-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="80749-113">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="80749-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80749-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80749-114">See also</span></span>

- [<span data-ttu-id="80749-115">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="80749-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="80749-116">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="80749-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

---
title: Chráněné členy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4574dffc3f9dd1b60d655bfde33a4ddc1a81d350
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44199736"
---
# <a name="protected-members"></a><span data-ttu-id="57245-102">Chráněné členy</span><span class="sxs-lookup"><span data-stu-id="57245-102">Protected Members</span></span>
<span data-ttu-id="57245-103">Chráněné členy samy o sobě neposkytuje žádné rozšíření, ale budou mít rozšiřitelnost prostřednictvím vytváření podtříd výkonnější.</span><span class="sxs-lookup"><span data-stu-id="57245-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="57245-104">Umožňuje vystavit rozšířené možnosti vlastního nastavení bez zbytečně komplikují hlavní veřejného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="57245-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="57245-105">Návrháři Framework muset být opatrní při práci s chráněné členy, protože název "protected" můžete poskytnout o zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="57245-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="57245-106">Všem uživatelům se bude moct podtřídy nezapečetěné třídy a přístupu k chráněným členům a stejné tak obranné drželi osvědčených kódovacích postupů použít pro veřejné členy platí pro chráněné členy.</span><span class="sxs-lookup"><span data-stu-id="57245-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="57245-107">**✓ CONSIDER** pomocí chráněné členy pro vlastní nastavení.</span><span class="sxs-lookup"><span data-stu-id="57245-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="57245-108">**✓ DO** považovat chráněné členy v nezapečetěných třídy jako veřejné pro účely analýzy zabezpečení, dokumentace a kompatibility.</span><span class="sxs-lookup"><span data-stu-id="57245-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="57245-109">Kdokoli na nich můžou dědit ze třídy a přistupovat k chráněným členům.</span><span class="sxs-lookup"><span data-stu-id="57245-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="57245-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="57245-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="57245-111">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="57245-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57245-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57245-112">See also</span></span>

- [<span data-ttu-id="57245-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="57245-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="57245-114">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="57245-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

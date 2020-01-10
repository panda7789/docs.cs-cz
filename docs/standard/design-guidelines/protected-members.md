---
title: Chránění členové
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 14ef02a760c9d4b77fe058334baffd63fcf29cfd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709098"
---
# <a name="protected-members"></a><span data-ttu-id="0e0fe-102">Chránění členové</span><span class="sxs-lookup"><span data-stu-id="0e0fe-102">Protected Members</span></span>
<span data-ttu-id="0e0fe-103">Chránění členové samy o sebe neposkytují žádné rozšiřitelnosti, ale mohou zvýšit výkon pomocí podtříd.</span><span class="sxs-lookup"><span data-stu-id="0e0fe-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="0e0fe-104">Dají se použít k vystavení pokročilých možností přizpůsobení, aniž by to zbytečně zkomplikovat hlavní veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0e0fe-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="0e0fe-105">Návrháři architektury musí být opatrní s chráněnými členy, protože název chráněný může mít nepravdivý smysl zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0e0fe-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="0e0fe-106">Kdokoli může podtřídit nezapečetěnou třídu a přistupovat k chráněným členům, takže všechny stejné postupy kódování obrannou linií použité pro veřejné členy se vztahují i na chráněné členy.</span><span class="sxs-lookup"><span data-stu-id="0e0fe-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="0e0fe-107">**✓ CONSIDER** pomocí chráněné členy pro vlastní nastavení.</span><span class="sxs-lookup"><span data-stu-id="0e0fe-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="0e0fe-108">**✓ DO** považovat chráněné členy v nezapečetěných třídy jako veřejné pro účely analýzy zabezpečení, dokumentace a kompatibility.</span><span class="sxs-lookup"><span data-stu-id="0e0fe-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="0e0fe-109">Kdokoli může dědit z třídy a přistupovat k chráněným členům.</span><span class="sxs-lookup"><span data-stu-id="0e0fe-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="0e0fe-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="0e0fe-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0e0fe-111">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="0e0fe-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e0fe-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e0fe-112">See also</span></span>

- [<span data-ttu-id="0e0fe-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="0e0fe-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="0e0fe-114">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="0e0fe-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

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
ms.openlocfilehash: 44d342662e1aaeb51f14470f354f2dadd9a6f18d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743645"
---
# <a name="protected-members"></a><span data-ttu-id="25118-102">Chránění členové</span><span class="sxs-lookup"><span data-stu-id="25118-102">Protected Members</span></span>
<span data-ttu-id="25118-103">Chránění členové samy o sebe neposkytují žádné rozšiřitelnosti, ale mohou zvýšit výkon pomocí podtříd.</span><span class="sxs-lookup"><span data-stu-id="25118-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="25118-104">Dají se použít k vystavení pokročilých možností přizpůsobení, aniž by to zbytečně zkomplikovat hlavní veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="25118-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="25118-105">Návrháři architektury musí být opatrní s chráněnými členy, protože název chráněný může mít nepravdivý smysl zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="25118-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="25118-106">Kdokoli může podtřídit nezapečetěnou třídu a přistupovat k chráněným členům, takže všechny stejné postupy kódování obrannou linií použité pro veřejné členy se vztahují i na chráněné členy.</span><span class="sxs-lookup"><span data-stu-id="25118-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="25118-107">✔️ Zvažte použití chráněných členů pro pokročilé přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="25118-107">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="25118-108">✔️ zacházet s chráněnými členy v nezapečetěných třídách jako veřejné pro účely zabezpečení, dokumentace a analýzy kompatibility.</span><span class="sxs-lookup"><span data-stu-id="25118-108">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="25118-109">Kdokoli může dědit z třídy a přistupovat k chráněným členům.</span><span class="sxs-lookup"><span data-stu-id="25118-109">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="25118-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="25118-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="25118-111">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="25118-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="25118-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="25118-112">See also</span></span>

- [<span data-ttu-id="25118-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="25118-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="25118-114">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="25118-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

---
title: Nezapečetěné třídy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6804a79e8beee1d42e313509966b46239e66c25f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743563"
---
# <a name="unsealed-classes"></a><span data-ttu-id="ab5c9-102">Nezapečetěné třídy</span><span class="sxs-lookup"><span data-stu-id="ab5c9-102">Unsealed Classes</span></span>
<span data-ttu-id="ab5c9-103">Zapečetěné třídy nelze dědit z a znemožňují rozšiřitelnost.</span><span class="sxs-lookup"><span data-stu-id="ab5c9-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="ab5c9-104">Naopak třídy, které lze zdědit z, se nazývají nezapečetěné třídy.</span><span class="sxs-lookup"><span data-stu-id="ab5c9-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>

 <span data-ttu-id="ab5c9-105">✔️ Zvažte použití nezapečetěných tříd bez přidaných virtuálních nebo chráněných členů jako skvělý způsob, jak poskytnout nenákladnou rozšiřitelnost rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ab5c9-105">✔️ CONSIDER using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>

 <span data-ttu-id="ab5c9-106">Vývojáři často chtějí zdědit z nezapečetěných tříd, aby mohli přidat praktické členy, jako jsou vlastní konstruktory, nové metody nebo přetížení metod.</span><span class="sxs-lookup"><span data-stu-id="ab5c9-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="ab5c9-107">Například `System.Messaging.MessageQueue` není zapečetěný, takže umožní uživatelům vytvářet vlastní fronty, které jsou ve výchozím nastavení pro konkrétní cestu fronty, nebo přidat vlastní metody, které zjednodušují rozhraní API pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="ab5c9-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>

 <span data-ttu-id="ab5c9-108">Třídy jsou ve výchozím nastavení ve většině programovacích jazyků nezapečetěné a toto je také Doporučená výchozí hodnota pro většinu tříd v rozhraních.</span><span class="sxs-lookup"><span data-stu-id="ab5c9-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="ab5c9-109">Rozšiřitelnost, kterou poskytují nezapečetěné typy, je mnohem vážíme od uživatelů rozhraní a poměrně levného, aby poskytovala z důvodu relativně nízkých nákladů na testování spojených s nezapečetěnými typy.</span><span class="sxs-lookup"><span data-stu-id="ab5c9-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>

 <span data-ttu-id="ab5c9-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="ab5c9-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ab5c9-111">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="ab5c9-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ab5c9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab5c9-112">See also</span></span>

- [<span data-ttu-id="ab5c9-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="ab5c9-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ab5c9-114">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="ab5c9-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="ab5c9-115">Zapečetění</span><span class="sxs-lookup"><span data-stu-id="ab5c9-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)

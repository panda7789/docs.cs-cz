---
title: Návrh statické třídy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: c906502ed071e8515f101996ec42a04772f72b12
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291926"
---
# <a name="static-class-design"></a><span data-ttu-id="fd999-102">Návrh statické třídy</span><span class="sxs-lookup"><span data-stu-id="fd999-102">Static Class Design</span></span>
<span data-ttu-id="fd999-103">Statická třída je definována jako třída, která obsahuje pouze statické členy (samozřejmě kromě členů instance zděděných z <xref:System.Object?displayProperty=nameWithType> a případně z privátního konstruktoru).</span><span class="sxs-lookup"><span data-stu-id="fd999-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="fd999-104">Některé jazyky poskytují integrovanou podporu pro statické třídy.</span><span class="sxs-lookup"><span data-stu-id="fd999-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="fd999-105">V jazyce C# 2,0 a novějším, pokud je třída deklarována jako statická, je zapečetěná, abstraktní a žádné členy instance nelze přepsat nebo deklarovat.</span><span class="sxs-lookup"><span data-stu-id="fd999-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>

 <span data-ttu-id="fd999-106">Statické třídy představují kompromis mezi čistě objektově orientovaným návrhem a jednoduchostí.</span><span class="sxs-lookup"><span data-stu-id="fd999-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="fd999-107">Obvykle se používají k poskytnutí zástupců pro jiné operace (například <xref:System.IO.File?displayProperty=nameWithType> ), držitelům rozšiřujících metod nebo funkcí, pro které je kompletní objektově orientované obálka neoprávněná (například <xref:System.Environment?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="fd999-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="fd999-108">✔️ použít statické třídy zřídka.</span><span class="sxs-lookup"><span data-stu-id="fd999-108">✔️ DO use static classes sparingly.</span></span>

 <span data-ttu-id="fd999-109">Statické třídy by měly být použity pouze jako podpůrné třídy pro objektově orientované jádro architektury.</span><span class="sxs-lookup"><span data-stu-id="fd999-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>

 <span data-ttu-id="fd999-110">❌Nepovažujte statické třídy za různé intervaly.</span><span class="sxs-lookup"><span data-stu-id="fd999-110">❌ DO NOT treat static classes as a miscellaneous bucket.</span></span>

 <span data-ttu-id="fd999-111">❌Nedeklarujte nebo přepište členy instance ve statických třídách.</span><span class="sxs-lookup"><span data-stu-id="fd999-111">❌ DO NOT declare or override instance members in static classes.</span></span>

 <span data-ttu-id="fd999-112">✔️ deklarovat statické třídy jako zapečetěné, abstraktní a přidat konstruktor privátní instance, pokud váš programovací jazyk nemá integrovanou podporu pro statické třídy.</span><span class="sxs-lookup"><span data-stu-id="fd999-112">✔️ DO declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>

 <span data-ttu-id="fd999-113">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="fd999-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="fd999-114">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="fd999-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="fd999-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd999-115">See also</span></span>

- [<span data-ttu-id="fd999-116">Pokyny pro návrh typů</span><span class="sxs-lookup"><span data-stu-id="fd999-116">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="fd999-117">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="fd999-117">Framework Design Guidelines</span></span>](index.md)

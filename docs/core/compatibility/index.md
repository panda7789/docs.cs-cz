---
title: Typy přerušujících změn – .NET Core
description: Přečtěte si, jak se .NET Core pokusí zachovat kompatibilitu pro vývojáře napříč verzemi .NET a jaký druh změny se považuje za zásadní změnu.
ms.date: 06/10/2019
ms.openlocfilehash: 5624a35a0d71224faf9adc5df2b02a529e650314
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567708"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="f921a-103">Změny ovlivňující kompatibilitu</span><span class="sxs-lookup"><span data-stu-id="f921a-103">Changes that affect compatibility</span></span>

<span data-ttu-id="f921a-104">V průběhu své historie se .NET pokusilo udržet vysokou úroveň kompatibility z verze na verzi a v různých charakterech rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="f921a-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="f921a-105">To platí i pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f921a-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="f921a-106">I když .NET Core se dá považovat za novou technologii, která je nezávislá na .NET Framework, dva hlavní faktory omezují schopnost .NET Core odchýlit se od .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f921a-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="f921a-107">Velký počet vývojářů byl buď původně vyvinutý, nebo pokračoval v vývoji .NET Frameworkch aplikací.</span><span class="sxs-lookup"><span data-stu-id="f921a-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="f921a-108">Očekávají konzistentní chování napříč implementacemi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="f921a-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="f921a-109">Projekty knihovny .NET Standard umožňují vývojářům vytvářet knihovny, které cílí na společná rozhraní API sdílená pomocí .NET Core a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f921a-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="f921a-110">Vývojáři očekávají, že se knihovna používaná v aplikaci .NET Core musí chovat stejně jako stejná knihovna, jakou používá aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f921a-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="f921a-111">Společně s kompatibilitou mezi implementacemi .NET očekávají vývojáři vysokou úroveň kompatibility napříč verzemi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f921a-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="f921a-112">Konkrétně kód napsaný pro starší verzi rozhraní .NET Core by měl běžet plynule v novější verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f921a-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="f921a-113">Mnoho vývojářů předpokládá, že nová rozhraní API nalezená v nově vydaných verzích rozhraní .NET Core by měla být také kompatibilní s předběžnými verzemi, ve kterých byla tato rozhraní API zavedena.</span><span class="sxs-lookup"><span data-stu-id="f921a-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="f921a-114">Tento článek popisuje kategorie změn kompatibility (nebo zásadní změny) a způsob, jakým tým .NET vyhodnocuje změny v každé z těchto kategorií.</span><span class="sxs-lookup"><span data-stu-id="f921a-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="f921a-115">Porozumění způsobu, jakým tým .NET přistupuje k možným nepřípadným změnám, je zvláště užitečné pro vývojáře, kteří otevřou žádosti o přijetí změn v úložišti [dotnet/corefx](https://github.com/dotnet/corefx) GitHubu, které upravují chování existujících rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="f921a-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests in the [dotnet/corefx](https://github.com/dotnet/corefx) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="f921a-116">Definici kategorií kompatibility, jako je binární kompatibilita a zpětná kompatibilita, najdete v tématu [přerušující kategorie změn](categories.md).</span><span class="sxs-lookup"><span data-stu-id="f921a-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="f921a-117">Následující části popisují kategorie změn provedených v rozhraních API .NET Core a jejich dopad na kompatibilitu aplikací.</span><span class="sxs-lookup"><span data-stu-id="f921a-117">The following sections describes the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="f921a-118">Ikona ✔️ označuje, že je povolen určitý druh změny, ❌ indikuje, že není povolený, a ❓ indikuje změnu, která může nebo nemusí být povolená.</span><span class="sxs-lookup"><span data-stu-id="f921a-118">The ✔️ icon indicates that a particular kind of change is allowed, ❌ indicates that it is disallowed, and  ❓ indicates a change that may or may not be allowed.</span></span> <span data-ttu-id="f921a-119">Změny v této poslední kategorii vyžadují posouzení a vyhodnocení toho, jak by bylo předchozí chování předvídatelné, zjevné a konzistentní.</span><span class="sxs-lookup"><span data-stu-id="f921a-119">Changes in this last category require judgement and an evaluation of how predictable, obvious, and consistent the previous behavior was.</span></span>

> [!NOTE]
> <span data-ttu-id="f921a-120">Kromě toho, že slouží jako vodítko, jak jsou vyhodnocovány změny knihoven .NET Core, mohou vývojáři knihovny použít také k vyhodnocení změn ve svých knihovnách, které cílí na více implementací a verzí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="f921a-120">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="f921a-121">Úpravy veřejné smlouvy</span><span class="sxs-lookup"><span data-stu-id="f921a-121">Modifications to the public contract</span></span>

<span data-ttu-id="f921a-122">Změny v této kategorii upravují oblast veřejného povrchu typu.</span><span class="sxs-lookup"><span data-stu-id="f921a-122">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="f921a-123">Většina změn v této kategorii není povolená, protože narušují *zpětnou kompatibilitu* (schopnost aplikace, která byla vyvinutá pomocí předchozí verze rozhraní API, aby se spustila bez překompilace na novější verzi).</span><span class="sxs-lookup"><span data-stu-id="f921a-123">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="f921a-124">Typy</span><span class="sxs-lookup"><span data-stu-id="f921a-124">Types</span></span>

- <span data-ttu-id="f921a-125">**✔️ odebrání implementace rozhraní z typu, když je rozhraní už implementované základním typem.**</span><span class="sxs-lookup"><span data-stu-id="f921a-125">**✔️ Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="f921a-126">**❓ Přidání nové implementace rozhraní do typu**</span><span class="sxs-lookup"><span data-stu-id="f921a-126">**❓ Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="f921a-127">Jedná se o přijatelnou změnu, protože nepříznivě neovlivní stávající klienty.</span><span class="sxs-lookup"><span data-stu-id="f921a-127">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="f921a-128">Všechny změny typu musí fungovat v rámci hranic přijatelných změn, které jsou zde definovány, aby nová implementace zůstala přijatelná.</span><span class="sxs-lookup"><span data-stu-id="f921a-128">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="f921a-129">Při přidávání rozhraní, která přímo ovlivňují schopnost návrháře nebo serializátoru vytvořit kód nebo data, která nelze spotřebovat na nižší úroveň, je nezbytné extrémní opatrnost.</span><span class="sxs-lookup"><span data-stu-id="f921a-129">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="f921a-130">Příkladem je <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f921a-130">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="f921a-131">**❓ Představení nové základní třídy**</span><span class="sxs-lookup"><span data-stu-id="f921a-131">**❓ Introducing a new base class**</span></span>

  <span data-ttu-id="f921a-132">Typ lze začlenit do hierarchie mezi dvěma existujícími typy, pokud nezavádí žádné nové [abstraktní](../../csharp/language-reference/keywords/abstract.md) členy nebo nemění sémantiku nebo chování stávajících typů.</span><span class="sxs-lookup"><span data-stu-id="f921a-132">A type can be introduced into an hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="f921a-133">Například v .NET Framework 2,0 se <xref:System.Data.Common.DbConnection> třída stala novou základní třídou pro <xref:System.Data.SqlClient.SqlConnection>, která byla dříve odvozena přímo od <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="f921a-133">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="f921a-134">**✔️ Přesunutí typu z jednoho sestavení na jiný**</span><span class="sxs-lookup"><span data-stu-id="f921a-134">**✔️ Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="f921a-135">Všimněte si, že *staré* sestavení musí být označeno <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>, které odkazuje na nové sestavení.</span><span class="sxs-lookup"><span data-stu-id="f921a-135">Note that the *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="f921a-136">**✔️ Změna typu [struktury](../../csharp/language-reference/keywords/struct.md) na typ `readonly struct`**</span><span class="sxs-lookup"><span data-stu-id="f921a-136">**✔️ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="f921a-137">Všimněte si, že změna typu `readonly struct` na typ `struct` není povolená.</span><span class="sxs-lookup"><span data-stu-id="f921a-137">Note that changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="f921a-138">**✔️ přidání klíčového slova [sealed](../../csharp/language-reference/keywords/sealed.md) nebo [abstract](../../csharp/language-reference/keywords/abstract.md) do typu, *Pokud nejsou k dispozici žádné (* veřejné nebo chráněné) konstruktory**</span><span class="sxs-lookup"><span data-stu-id="f921a-138">**✔️ Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="f921a-139">**✔️ rozšíření viditelnosti typu**</span><span class="sxs-lookup"><span data-stu-id="f921a-139">**✔️ Expanding the visibility of a type**</span></span>

- <span data-ttu-id="f921a-140">**❌ Změna oboru názvů nebo názvu typu**</span><span class="sxs-lookup"><span data-stu-id="f921a-140">**❌ Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="f921a-141">**❌ přejmenování nebo odebrání veřejného typu**</span><span class="sxs-lookup"><span data-stu-id="f921a-141">**❌ Renaming or removing a public type**</span></span>

   <span data-ttu-id="f921a-142">Tím dojde k zalomení veškerého kódu, který používá přejmenovaný nebo odebraný typ.</span><span class="sxs-lookup"><span data-stu-id="f921a-142">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="f921a-143">**❌ Změna základního typu výčtu**</span><span class="sxs-lookup"><span data-stu-id="f921a-143">**❌ Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="f921a-144">Toto je zásadní změna v době kompilace a chování a také binární zásadní změna, která může nastavit argumenty atributu jako neanalyzovatelné.</span><span class="sxs-lookup"><span data-stu-id="f921a-144">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="f921a-145">**❌ zapečetění typu, který se dřív nezapečetěný**</span><span class="sxs-lookup"><span data-stu-id="f921a-145">**❌ Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="f921a-146">**❌ přidání rozhraní do sady základních typů rozhraní**</span><span class="sxs-lookup"><span data-stu-id="f921a-146">**❌ Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="f921a-147">Pokud rozhraní implementuje rozhraní, které dříve neimplementovalo, všechny typy, které implementují původní verzi rozhraní, jsou přerušeny.</span><span class="sxs-lookup"><span data-stu-id="f921a-147">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="f921a-148">**❓ Odebrání třídy ze sady základních tříd nebo z rozhraní ze sady implementovaných rozhraní**</span><span class="sxs-lookup"><span data-stu-id="f921a-148">**❓ Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="f921a-149">Pravidlo pro odebrání rozhraní obsahuje jednu výjimku: můžete přidat implementaci rozhraní, které je odvozeno z odebraného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f921a-149">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="f921a-150">Můžete například odebrat <xref:System.IDisposable>, pokud typ nebo rozhraní nyní implementuje <xref:System.ComponentModel.IComponent>, které implementuje <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="f921a-150">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="f921a-151">**❌ Změna typu `readonly struct` na typ [struktury](../../csharp/language-reference/keywords/struct.md)**</span><span class="sxs-lookup"><span data-stu-id="f921a-151">**❌ Changing a `readonly struct` type to a [struct](../../csharp/language-reference/keywords/struct.md) type**</span></span>

  <span data-ttu-id="f921a-152">Všimněte si, že změna typu `struct` na typ `readonly struct` je povolena.</span><span class="sxs-lookup"><span data-stu-id="f921a-152">Note that the change of a `struct` type to a `readonly struct` type is allowed.</span></span>

- <span data-ttu-id="f921a-153">**❌ Změna typu [struktury](../../csharp/language-reference/keywords/struct.md) na typ `ref struct` a naopak**</span><span class="sxs-lookup"><span data-stu-id="f921a-153">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="f921a-154">**❌ snížení viditelnosti typu**</span><span class="sxs-lookup"><span data-stu-id="f921a-154">**❌ Reducing the visibility of a type**</span></span>

   <span data-ttu-id="f921a-155">Nicméně zvýšení viditelnosti typu je povoleno.</span><span class="sxs-lookup"><span data-stu-id="f921a-155">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="f921a-156">Členové</span><span class="sxs-lookup"><span data-stu-id="f921a-156">Members</span></span>

- <span data-ttu-id="f921a-157">**✔️ rozšíření viditelnosti členu, který není [virtuální](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="f921a-157">**✔️ Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="f921a-158">**✔️ Přidání abstraktního člena k veřejnému typu, který nemá žádné *přístupné* (veřejné nebo chráněné) konstruktory nebo je typ [zapečetěný](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="f921a-158">**✔️ Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="f921a-159">Nicméně přidání abstraktního člena do typu, který má přístupné (veřejné nebo chráněné) konstruktory a není `sealed` není povoleno.</span><span class="sxs-lookup"><span data-stu-id="f921a-159">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="f921a-160">**✔️ omezit viditelnost [chráněného](../../csharp/language-reference/keywords/protected.md) člena, když typ nemá žádné přístupné (veřejné nebo chráněné) konstruktory nebo je typ [zapečetěný](../../csharp/language-reference/keywords/sealed.md) .**</span><span class="sxs-lookup"><span data-stu-id="f921a-160">**✔️ Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="f921a-161">**✔️ přesunu člena do třídy vyšší v hierarchii, než je typ, ze kterého byl odebrán**</span><span class="sxs-lookup"><span data-stu-id="f921a-161">**✔️ Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="f921a-162">**✔️ Přidání nebo odebrání přepsání**</span><span class="sxs-lookup"><span data-stu-id="f921a-162">**✔️ Adding or removing an override**</span></span>

  <span data-ttu-id="f921a-163">Všimněte si, že zavedení přepsání může způsobit, že předchozí příjemci přeskočí přepsání při volání [základny](../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="f921a-163">Note that introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="f921a-164">**✔️ Přidání konstruktoru do třídy spolu s konstruktorem bez parametrů, pokud třída předtím neměla žádné konstruktory**</span><span class="sxs-lookup"><span data-stu-id="f921a-164">**✔️ Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="f921a-165">Nicméně přidání konstruktoru do třídy, která dříve neměla žádné konstruktory bez přidání konstruktoru *bez* parametrů, není povoleno.</span><span class="sxs-lookup"><span data-stu-id="f921a-165">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="f921a-166">**✔️ Změna členu z [abstract](../../csharp/language-reference/keywords/abstract.md) na [Virtual](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="f921a-166">**✔️ Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="f921a-167">**✔️ Změna hodnoty z `ref readonly` na `ref` návratovou hodnotu (s výjimkou virtuálních metod nebo rozhraní)**</span><span class="sxs-lookup"><span data-stu-id="f921a-167">**✔️ Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="f921a-168">**✔️ odstranění [jen pro čtení](../../csharp/language-reference/keywords/readonly.md) z pole, pokud statický typ pole není proměnlivý typ hodnoty.**</span><span class="sxs-lookup"><span data-stu-id="f921a-168">**✔️ Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="f921a-169">**✔️ volání nové události, která nebyla dříve definovaná.**</span><span class="sxs-lookup"><span data-stu-id="f921a-169">**✔️ Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="f921a-170">**❓ Přidání nového pole instance do typu**</span><span class="sxs-lookup"><span data-stu-id="f921a-170">**❓ Adding a new instance field to a type**</span></span>

   <span data-ttu-id="f921a-171">Tato změna ovlivňuje serializaci.</span><span class="sxs-lookup"><span data-stu-id="f921a-171">This change impacts serialization.</span></span>

- <span data-ttu-id="f921a-172">**❌ přejmenování nebo odebrání veřejného členu nebo parametru**</span><span class="sxs-lookup"><span data-stu-id="f921a-172">**❌ Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="f921a-173">Tím dojde k rozdělení veškerého kódu, který používá přejmenovaný nebo odebraný člen nebo parametr.</span><span class="sxs-lookup"><span data-stu-id="f921a-173">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="f921a-174">Všimněte si, že to zahrnuje odebrání nebo přejmenování metody getter nebo setter z vlastnosti a také přejmenování nebo odebrání členů výčtu.</span><span class="sxs-lookup"><span data-stu-id="f921a-174">Note that this includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="f921a-175">**❌ přidání člena do rozhraní**</span><span class="sxs-lookup"><span data-stu-id="f921a-175">**❌ Adding a member to an interface**</span></span>

- <span data-ttu-id="f921a-176">**❌ Změna hodnoty veřejné konstanty nebo člena výčtu**</span><span class="sxs-lookup"><span data-stu-id="f921a-176">**❌ Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="f921a-177">**❌ Změna typu vlastnosti, pole, parametru nebo návratové hodnoty**</span><span class="sxs-lookup"><span data-stu-id="f921a-177">**❌ Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="f921a-178">**❌ přidání, odebrání nebo změna pořadí parametrů**</span><span class="sxs-lookup"><span data-stu-id="f921a-178">**❌ Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="f921a-179">**❌ přidání nebo odebrání klíčového slova [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) nebo [ref](../../csharp/language-reference/keywords/ref.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="f921a-179">**❌ Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="f921a-180">**❌ Přejmenování parametru (včetně změny jeho velikosti)**</span><span class="sxs-lookup"><span data-stu-id="f921a-180">**❌ Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="f921a-181">To se považuje za porušení dvou důvodů:</span><span class="sxs-lookup"><span data-stu-id="f921a-181">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="f921a-182">Dojde k přerušení scénářů s pozdní vazbou, jako je funkce pozdní vazby [](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) v Visual Basic C#a dynamické v.</span><span class="sxs-lookup"><span data-stu-id="f921a-182">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="f921a-183">Pokud vývojáři používají [pojmenované argumenty](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments), dojde k přerušení [kompatibility zdrojů](categories.md#source-compatibility) .</span><span class="sxs-lookup"><span data-stu-id="f921a-183">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="f921a-184">**❌ změna ze `ref` návratové hodnoty na `ref readonly` návratovou hodnotu**</span><span class="sxs-lookup"><span data-stu-id="f921a-184">**❌ Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="f921a-185">**❌️ změna z `ref readonly` na `ref` návratovou hodnotu ve virtuální metodě nebo rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="f921a-185">**❌️ Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="f921a-186">**❌ přidávání nebo odebírání [abstraktu](../../csharp/language-reference/keywords/abstract.md) ze člena**</span><span class="sxs-lookup"><span data-stu-id="f921a-186">**❌ Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="f921a-187">**❌ odebrání klíčového slova [Virtual](../../csharp/language-reference/keywords/virtual.md) ze člena**</span><span class="sxs-lookup"><span data-stu-id="f921a-187">**❌ Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="f921a-188">I když se tato často nejedná o zásadní změnu C# , protože kompilátor chce vygenerovat instrukce [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) pro volání nevirtuálních metod (`callvirt` provádí kontrolu hodnot null, zatímco normální volání ne), toto chování není inproměnná z několika důvodů:</span><span class="sxs-lookup"><span data-stu-id="f921a-188">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="f921a-189">C#není jediným jazykem, který cílí na .NET.</span><span class="sxs-lookup"><span data-stu-id="f921a-189">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="f921a-190">C# Kompilátor stále častěji snaží optimalizovat `callvirt` na normální volání, kdykoli je cílová metoda nevirtuální a pravděpodobně není null (například metoda, ke které se přistupoval prostřednictvím [operátoru rozšíření?. null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span><span class="sxs-lookup"><span data-stu-id="f921a-190">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="f921a-191">Vytvořením metody Virtual by kód příjemce často ukončil volání, které není prakticky.</span><span class="sxs-lookup"><span data-stu-id="f921a-191">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="f921a-192">**❌ přidání klíčového slova [Virtual](../../csharp/language-reference/keywords/virtual.md) do člena**</span><span class="sxs-lookup"><span data-stu-id="f921a-192">**❌ Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="f921a-193">**❌ vytvoření abstrakce virtuálního členu**</span><span class="sxs-lookup"><span data-stu-id="f921a-193">**❌ Making a virtual member abstract**</span></span>

  <span data-ttu-id="f921a-194">[Virtuální člen](../../csharp/language-reference/keywords/virtual.md) poskytuje implementaci metody, kterou *lze* přepsat odvozenou třídou.</span><span class="sxs-lookup"><span data-stu-id="f921a-194">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="f921a-195">[Abstraktní člen](../../csharp/language-reference/keywords/abstract.md) neposkytuje žádnou implementaci a *musí být* přepsán.</span><span class="sxs-lookup"><span data-stu-id="f921a-195">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="f921a-196">**❌ přidání abstraktního člena k veřejnému typu, který má přístupné (veřejné nebo chráněné) konstruktory, které nejsou [zapečetěné](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="f921a-196">**❌ Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="f921a-197">**❌ přidání nebo odebrání klíčového slova [static](../../csharp/language-reference/keywords/static.md) ze člena**</span><span class="sxs-lookup"><span data-stu-id="f921a-197">**❌ Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="f921a-198">**❌ přidání přetížení, které vylučuje existující přetížení a definuje jiné chování**</span><span class="sxs-lookup"><span data-stu-id="f921a-198">**❌ Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="f921a-199">Tím dojde k přerušení stávajících klientů vázaných na předchozí přetížení.</span><span class="sxs-lookup"><span data-stu-id="f921a-199">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="f921a-200">Například pokud má třída jedinou verzi metody, která přijímá <xref:System.UInt32>, existující příjemce se úspěšně připojí k tomuto přetížení při předávání hodnoty <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="f921a-200">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="f921a-201">Nicméně pokud přidáte přetížení, které přijímá <xref:System.Int32>, při rekompilování nebo použití pozdní vazby nyní kompilátor vytvoří vazbu k novému přetížení.</span><span class="sxs-lookup"><span data-stu-id="f921a-201">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="f921a-202">Pokud dojde k různým výsledkům chování, jedná se o zásadní změnu.</span><span class="sxs-lookup"><span data-stu-id="f921a-202">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="f921a-203">**❌ přidání konstruktoru do třídy, která dříve neměla žádný konstruktor bez přidání konstruktoru bez parametrů**</span><span class="sxs-lookup"><span data-stu-id="f921a-203">**❌ Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="f921a-204">**❌️ přidání [ReadOnly](../../csharp/language-reference/keywords/readonly.md) do pole**</span><span class="sxs-lookup"><span data-stu-id="f921a-204">**❌️ Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="f921a-205">**❌ snížení viditelnosti člena**</span><span class="sxs-lookup"><span data-stu-id="f921a-205">**❌ Reducing the visibility of a member**</span></span>

   <span data-ttu-id="f921a-206">To zahrnuje snížení viditelnosti [chráněného](../../csharp/language-reference/keywords/protected.md) člena, pokud jsou *přístupné* (veřejné nebo chráněné) konstruktory a *typ není* [zapečetěný](../../csharp/language-reference/keywords/sealed.md).</span><span class="sxs-lookup"><span data-stu-id="f921a-206">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (public or protected) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="f921a-207">V takovém případě se omezení viditelnosti chráněného člena povoluje.</span><span class="sxs-lookup"><span data-stu-id="f921a-207">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="f921a-208">Všimněte si, že zvýšení viditelnosti člena je povoleno.</span><span class="sxs-lookup"><span data-stu-id="f921a-208">Note that increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="f921a-209">**❌ Změna typu člena**</span><span class="sxs-lookup"><span data-stu-id="f921a-209">**❌ Changing the type of a member**</span></span>

   <span data-ttu-id="f921a-210">Vrácenou hodnotu metody nebo typu pole nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="f921a-210">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="f921a-211">Například podpis metody, která vrací <xref:System.Object>, nelze změnit tak, aby vracela <xref:System.String>, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="f921a-211">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="f921a-212">**❌ přidání pole do struktury, která dřív neměla žádný stav**</span><span class="sxs-lookup"><span data-stu-id="f921a-212">**❌ Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="f921a-213">Pravidla pro jednoznačné přiřazení umožňují použití neinicializovaných proměnných, pokud typ proměnné je Bezstavová struktura.</span><span class="sxs-lookup"><span data-stu-id="f921a-213">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="f921a-214">Pokud je struktura nastavená jako stavová, může kód končit neinicializovanými daty.</span><span class="sxs-lookup"><span data-stu-id="f921a-214">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="f921a-215">To může být i poškození zdroje a binární změna.</span><span class="sxs-lookup"><span data-stu-id="f921a-215">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="f921a-216">**❌ vypálení existující události, když nebyla nikdy aktivována**</span><span class="sxs-lookup"><span data-stu-id="f921a-216">**❌ Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="f921a-217">Změny chování</span><span class="sxs-lookup"><span data-stu-id="f921a-217">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="f921a-218">Sestavení</span><span class="sxs-lookup"><span data-stu-id="f921a-218">Assemblies</span></span>

- <span data-ttu-id="f921a-219">**✔️ přenos sestavení v případě, že jsou stejné platformy stále podporovány**</span><span class="sxs-lookup"><span data-stu-id="f921a-219">**✔️ Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="f921a-220">**❌ Změna názvu sestavení**</span><span class="sxs-lookup"><span data-stu-id="f921a-220">**❌ Changing the name of an assembly**</span></span>
- <span data-ttu-id="f921a-221">**❌ změna veřejného klíče sestavení**</span><span class="sxs-lookup"><span data-stu-id="f921a-221">**❌ Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="f921a-222">Vlastnosti, pole, parametry a návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="f921a-222">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="f921a-223">**✔️ Změna hodnoty vlastnosti, pole, návratové hodnoty nebo parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na více odvozený typ**</span><span class="sxs-lookup"><span data-stu-id="f921a-223">**✔️ Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="f921a-224">Například metoda, která vrací typ <xref:System.Object> může vracet instanci <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f921a-224">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="f921a-225">(Signatura metody se ale nemůže změnit.)</span><span class="sxs-lookup"><span data-stu-id="f921a-225">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="f921a-226">**✔️ zvýšení rozsahu přijatelných hodnot pro vlastnost nebo parametr, pokud člen není [virtuální](../../csharp/language-reference/keywords/virtual.md) .**</span><span class="sxs-lookup"><span data-stu-id="f921a-226">**✔️ Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="f921a-227">Všimněte si, že zatímco rozsah hodnot, které lze předat metodě nebo které mohou být vráceny členem, lze rozšířit, parametr nebo typ člena nemůže.</span><span class="sxs-lookup"><span data-stu-id="f921a-227">Note that while the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="f921a-228">Například zatímco hodnoty předané metodě lze rozšířit z 0-124 na 0-255, typ parametru nemůže být změněn z <xref:System.Byte> na <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="f921a-228">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="f921a-229">**❌ zvýšení rozsahu přijatelných hodnot pro vlastnost nebo parametr, pokud je člen [virtuální](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="f921a-229">**❌ Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="f921a-230">Tato změna rozdělí existující přepsané členy, které nebudou správně fungovat pro rozšířený rozsah hodnot.</span><span class="sxs-lookup"><span data-stu-id="f921a-230">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="f921a-231">**❌ snížení rozsahu přijatelných hodnot pro vlastnost nebo parametr**</span><span class="sxs-lookup"><span data-stu-id="f921a-231">**❌ Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="f921a-232">**❌ zvýšení rozsahu vrácených hodnot pro vlastnost, pole, návratovou hodnotu nebo [výstupní](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**</span><span class="sxs-lookup"><span data-stu-id="f921a-232">**❌ Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="f921a-233">**❌ změnu vrácených hodnot pro vlastnost, pole, návratovou hodnotu metody nebo [výstupní](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**</span><span class="sxs-lookup"><span data-stu-id="f921a-233">**❌ Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="f921a-234">**❌ Změna výchozí hodnoty vlastnosti, pole nebo parametru**</span><span class="sxs-lookup"><span data-stu-id="f921a-234">**❌ Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="f921a-235">**❌ měnící přesnost číselné návratové hodnoty**</span><span class="sxs-lookup"><span data-stu-id="f921a-235">**❌ Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="f921a-236">**❓ Změnu v analýze vstupu a vyvolání nových výjimek (i v případě, že se v dokumentaci nezadá chování při analýze)**</span><span class="sxs-lookup"><span data-stu-id="f921a-236">**❓ A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="f921a-237">Výjimky</span><span class="sxs-lookup"><span data-stu-id="f921a-237">Exceptions</span></span>

- <span data-ttu-id="f921a-238">**✔️ vyvolání více odvozené výjimky, než je stávající výjimka**</span><span class="sxs-lookup"><span data-stu-id="f921a-238">**✔️ Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="f921a-239">Vzhledem k tomu, že nová výjimka je podtřídou existující výjimky, pokračuje zpracování předchozí kódu zpracováním výjimky.</span><span class="sxs-lookup"><span data-stu-id="f921a-239">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="f921a-240">Například v .NET Framework 4 začaly metody vytváření a načítání jazykové verze vyvolávat <xref:System.Globalization.CultureNotFoundException> namísto <xref:System.ArgumentException>, pokud nebyla nalezena jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="f921a-240">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="f921a-241">Vzhledem k tomu, že <xref:System.Globalization.CultureNotFoundException> jsou odvozeny z <xref:System.ArgumentException>, jedná se o přijatelnou změnu.</span><span class="sxs-lookup"><span data-stu-id="f921a-241">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="f921a-242">**✔️ vyvolává konkrétnější výjimku než <xref:System.NotSupportedException>, <xref:System.NotImplementedException><xref:System.NullReferenceException>**</span><span class="sxs-lookup"><span data-stu-id="f921a-242">**✔️ Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="f921a-243">**✔️a se vyvolala výjimka, která je považována za neodstranitelnou.**</span><span class="sxs-lookup"><span data-stu-id="f921a-243">**✔️ Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="f921a-244">Neodstranitelné výjimky by neměly být zachyceny, ale místo toho by měly být zpracovány pomocí obslužné rutiny catch na vysoké úrovni.</span><span class="sxs-lookup"><span data-stu-id="f921a-244">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="f921a-245">Proto se neočekává, že uživatelé budou mít kód, který tyto explicitní výjimky zachytí.</span><span class="sxs-lookup"><span data-stu-id="f921a-245">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="f921a-246">Neobnovitelné výjimky jsou:</span><span class="sxs-lookup"><span data-stu-id="f921a-246">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="f921a-247">**✔️ vyvolání nové výjimky v nové cestě kódu**</span><span class="sxs-lookup"><span data-stu-id="f921a-247">**✔️ Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="f921a-248">Výjimka se musí vztahovat pouze k nové cestě kódu, která je spuštěna s novými hodnotami parametrů nebo stavem, a nelze ji spustit pomocí stávajícího kódu, který cílí na předchozí verzi.</span><span class="sxs-lookup"><span data-stu-id="f921a-248">The exception must apply only to a new code-path which is executed with new parameter values or state, and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="f921a-249">**✔️ odebrání výjimky pro zajištění robustnějšího chování nebo nových scénářů**</span><span class="sxs-lookup"><span data-stu-id="f921a-249">**✔️ Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="f921a-250">Například `Divide` metoda, která dříve zpracovala pouze kladné hodnoty a vyvolala <xref:System.ArgumentOutOfRangeException> jinak může být změněna tak, aby podporovala záporné i kladné hodnoty bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="f921a-250">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="f921a-251">**✔️ Změna textu chybové zprávy**</span><span class="sxs-lookup"><span data-stu-id="f921a-251">**✔️ Changing the text of an error message**</span></span>

  <span data-ttu-id="f921a-252">Vývojáři by neměli spoléhat na text chybových zpráv, které se také mění v závislosti na jazykové verzi uživatele.</span><span class="sxs-lookup"><span data-stu-id="f921a-252">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="f921a-253">**❌ vyvolání výjimky v jakémkoli jiném případě, který není uveden výše.**</span><span class="sxs-lookup"><span data-stu-id="f921a-253">**❌ Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="f921a-254">**❌ odebrání výjimky v jakémkoli jiném případě, který není uvedený výše**</span><span class="sxs-lookup"><span data-stu-id="f921a-254">**❌ Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="f921a-255">Atributy</span><span class="sxs-lookup"><span data-stu-id="f921a-255">Attributes</span></span>

- <span data-ttu-id="f921a-256">**✔️ Změna hodnoty atributu, který *není pozorovatelný***</span><span class="sxs-lookup"><span data-stu-id="f921a-256">**✔️ Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="f921a-257">**❌ Změna hodnoty atributu, který *je* pozorovatelný**</span><span class="sxs-lookup"><span data-stu-id="f921a-257">**❌ Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="f921a-258">**❓ Odebrání atributu**</span><span class="sxs-lookup"><span data-stu-id="f921a-258">**❓ Removing an attribute**</span></span>

  <span data-ttu-id="f921a-259">Ve většině případů je odebrání atributu (například <xref:System.NonSerializedAttribute>) zásadní změnou.</span><span class="sxs-lookup"><span data-stu-id="f921a-259">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="f921a-260">Podpora platforem</span><span class="sxs-lookup"><span data-stu-id="f921a-260">Platform support</span></span>

- <span data-ttu-id="f921a-261">**✔️ podporující operaci na platformě, která nebyla dřív podporovaná**</span><span class="sxs-lookup"><span data-stu-id="f921a-261">**✔️ Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="f921a-262">**❌ nepodporují nebo ještě nevyžadují konkrétní aktualizaci Service Pack pro operaci, která byla dřív podporovaná na platformě.**</span><span class="sxs-lookup"><span data-stu-id="f921a-262">**❌ Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="f921a-263">Změny interní implementace</span><span class="sxs-lookup"><span data-stu-id="f921a-263">Internal implementation changes</span></span>

- <span data-ttu-id="f921a-264">**❓ Změna oblasti povrchu interního typu**</span><span class="sxs-lookup"><span data-stu-id="f921a-264">**❓ Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="f921a-265">Tyto změny jsou obecně povoleny, i když přeruší soukromý odraz.</span><span class="sxs-lookup"><span data-stu-id="f921a-265">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="f921a-266">V některých případech, kde jsou oblíbené knihovny třetích stran nebo velký počet vývojářů závislé na interních rozhraních API, nemusí být tyto změny povolené.</span><span class="sxs-lookup"><span data-stu-id="f921a-266">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="f921a-267">**❓ Změna interní implementace člena**</span><span class="sxs-lookup"><span data-stu-id="f921a-267">**❓ Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="f921a-268">Tyto změny jsou obecně povoleny, i když přeruší soukromý odraz.</span><span class="sxs-lookup"><span data-stu-id="f921a-268">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="f921a-269">V některých případech, kde kód zákazníka často závisí na soukromé reflexi nebo kde změna zavádí nezamýšlené vedlejší účinky, nemusí být tyto změny povoleny.</span><span class="sxs-lookup"><span data-stu-id="f921a-269">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="f921a-270">**✔️ zlepšení výkonu operace**</span><span class="sxs-lookup"><span data-stu-id="f921a-270">**✔️ Improving the performance of an operation**</span></span>

   <span data-ttu-id="f921a-271">Možnost upravit výkon operace je zásadní, ale tyto změny mohou přerušit kód, který spoléhá na aktuální rychlost operace.</span><span class="sxs-lookup"><span data-stu-id="f921a-271">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="f921a-272">To platí zejména pro kód, který závisí na časování asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="f921a-272">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="f921a-273">Všimněte si, že změna výkonu by neměla mít žádný vliv na jiné chování rozhraní API. v opačném případě bude změna zálomena.</span><span class="sxs-lookup"><span data-stu-id="f921a-273">Note that the performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="f921a-274">**✔️ nepřímo (a často nepříznivě) měnit výkon operace.**</span><span class="sxs-lookup"><span data-stu-id="f921a-274">**✔️ Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="f921a-275">Pokud se změna nedělí z nějakého jiného důvodu jako porušení, je to přijatelné.</span><span class="sxs-lookup"><span data-stu-id="f921a-275">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="f921a-276">Často je potřeba provést akce, které mohou zahrnovat dodatečné operace nebo které přidávají nové funkce.</span><span class="sxs-lookup"><span data-stu-id="f921a-276">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="f921a-277">To bude téměř vždy mít vliv na výkon, ale může být nezbytné, aby rozhraní API fungovalo podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="f921a-277">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="f921a-278">**❌ změna synchronního rozhraní API na asynchronní (a naopak)**</span><span class="sxs-lookup"><span data-stu-id="f921a-278">**❌ Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="f921a-279">Změny kódu</span><span class="sxs-lookup"><span data-stu-id="f921a-279">Code changes</span></span>

- <span data-ttu-id="f921a-280">**✔️ Přidání [parametrů](../../csharp/language-reference/keywords/params.md) do parametru**</span><span class="sxs-lookup"><span data-stu-id="f921a-280">**✔️ Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="f921a-281">**❌ změnu [struktury](../../csharp/language-reference/keywords/struct.md) na [třídu](../../csharp/language-reference/keywords/class.md) a naopak**</span><span class="sxs-lookup"><span data-stu-id="f921a-281">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="f921a-282">**❌ přidání klíčového slova [checked](../../csharp/language-reference/keywords/virtual.md) do bloku kódu**</span><span class="sxs-lookup"><span data-stu-id="f921a-282">**❌ Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="f921a-283">Tato změna může způsobit, že kód, který dřív provedl k vyvolání <xref:System.OverflowException> a je nepřijatelný.</span><span class="sxs-lookup"><span data-stu-id="f921a-283">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="f921a-284">**❌ odebírání [parametrů](../../csharp/language-reference/keywords/params.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="f921a-284">**❌ Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="f921a-285">**❌ Změna pořadí, ve kterém jsou události aktivovány**</span><span class="sxs-lookup"><span data-stu-id="f921a-285">**❌ Changing the order in which events are fired**</span></span>

  <span data-ttu-id="f921a-286">Vývojáři mohou rozumně očekávat, že události budou aktivovány ve stejném pořadí a kód pro vývojáře často závisí na pořadí, ve kterém jsou události vyvolány.</span><span class="sxs-lookup"><span data-stu-id="f921a-286">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="f921a-287">**❌ odebrání vyvolání události na dané akci**</span><span class="sxs-lookup"><span data-stu-id="f921a-287">**❌ Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="f921a-288">**❌ změnu počtu volání daných událostí**</span><span class="sxs-lookup"><span data-stu-id="f921a-288">**❌ Changing the number of times given events are called**</span></span>

- <span data-ttu-id="f921a-289">**❌ přidání <xref:System.FlagsAttribute> do výčtového typu**</span><span class="sxs-lookup"><span data-stu-id="f921a-289">**❌ Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>

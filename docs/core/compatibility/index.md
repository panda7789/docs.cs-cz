---
title: Typy přerušujících změn
description: Přečtěte si, jak se .NET Core pokusí zachovat kompatibilitu pro vývojáře napříč verzemi .NET a jaký druh změny se považuje za zásadní změnu.
ms.date: 06/10/2019
ms.openlocfilehash: bf0cc35d69e6bb501640455604a99a1f48962c4a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628589"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="7d954-103">Změny ovlivňující kompatibilitu</span><span class="sxs-lookup"><span data-stu-id="7d954-103">Changes that affect compatibility</span></span>

<span data-ttu-id="7d954-104">V průběhu své historie se .NET pokusilo udržet vysokou úroveň kompatibility z verze na verzi a v různých charakterech rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="7d954-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="7d954-105">To platí i pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7d954-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="7d954-106">I když .NET Core se dá považovat za novou technologii, která je nezávislá na .NET Framework, dva hlavní faktory omezují schopnost .NET Core odchýlit se od .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7d954-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="7d954-107">Velký počet vývojářů byl buď původně vyvinutý, nebo pokračoval v vývoji .NET Frameworkch aplikací.</span><span class="sxs-lookup"><span data-stu-id="7d954-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="7d954-108">Očekávají konzistentní chování napříč implementacemi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="7d954-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="7d954-109">Projekty knihovny .NET Standard umožňují vývojářům vytvářet knihovny, které cílí na společná rozhraní API sdílená pomocí .NET Core a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d954-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="7d954-110">Vývojáři očekávají, že se knihovna používaná v aplikaci .NET Core musí chovat stejně jako stejná knihovna, jakou používá aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d954-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="7d954-111">Společně s kompatibilitou mezi implementacemi .NET očekávají vývojáři vysokou úroveň kompatibility napříč verzemi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7d954-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="7d954-112">Konkrétně kód napsaný pro starší verzi rozhraní .NET Core by měl běžet plynule v novější verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7d954-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="7d954-113">Mnoho vývojářů předpokládá, že nová rozhraní API nalezená v nově vydaných verzích rozhraní .NET Core by měla být také kompatibilní s předběžnými verzemi, ve kterých byla tato rozhraní API zavedena.</span><span class="sxs-lookup"><span data-stu-id="7d954-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="7d954-114">Tento článek popisuje kategorie změn kompatibility (nebo zásadní změny) a způsob, jakým tým .NET vyhodnocuje změny v každé z těchto kategorií.</span><span class="sxs-lookup"><span data-stu-id="7d954-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="7d954-115">Porozumění způsobu, jakým tým .NET přistupuje k možným nepřípadným změnám, je zvláště užitečné pro vývojáře, kteří otevřou žádosti o přijetí změn v úložišti GitHubu [a modulu runtime](https://github.com/dotnet/runtime) , které upravují chování existujících rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7d954-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests in the [dotnet/runtime](https://github.com/dotnet/runtime) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="7d954-116">Definici kategorií kompatibility, jako je binární kompatibilita a zpětná kompatibilita, najdete v tématu [přerušující kategorie změn](categories.md).</span><span class="sxs-lookup"><span data-stu-id="7d954-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="7d954-117">Následující části popisují kategorie změn provedených v rozhraních API .NET Core a jejich dopad na kompatibilitu aplikací.</span><span class="sxs-lookup"><span data-stu-id="7d954-117">The following sections describe the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="7d954-118">Změny jsou buď povolené ✔️, nepovolené ❌, nebo vyžadují rozhodnutí a hodnocení, jak předvídatelné, zjevné a konzistentní předchozí chování byly ❓.</span><span class="sxs-lookup"><span data-stu-id="7d954-118">Changes are either allowed ✔️, disallowed ❌, or require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was ❓.</span></span>

> [!NOTE]
> <span data-ttu-id="7d954-119">Kromě toho, že slouží jako vodítko, jak jsou vyhodnocovány změny knihoven .NET Core, mohou vývojáři knihovny použít také k vyhodnocení změn ve svých knihovnách, které cílí na více implementací a verzí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="7d954-119">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="7d954-120">Úpravy veřejné smlouvy</span><span class="sxs-lookup"><span data-stu-id="7d954-120">Modifications to the public contract</span></span>

<span data-ttu-id="7d954-121">Změny v této kategorii upravují oblast veřejného povrchu typu.</span><span class="sxs-lookup"><span data-stu-id="7d954-121">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="7d954-122">Většina změn v této kategorii není povolená, protože narušují *zpětnou kompatibilitu* (schopnost aplikace, která byla vyvinutá pomocí předchozí verze rozhraní API, aby se spustila bez překompilace na novější verzi).</span><span class="sxs-lookup"><span data-stu-id="7d954-122">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="7d954-123">Typy</span><span class="sxs-lookup"><span data-stu-id="7d954-123">Types</span></span>

- <span data-ttu-id="7d954-124">✔️ **povoleno: odebrání implementace rozhraní z typu, když je rozhraní již implementováno pomocí základního typu**</span><span class="sxs-lookup"><span data-stu-id="7d954-124">✔️ **ALLOWED: Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="7d954-125">❓ **Vyžaduje rozhodnutí: Přidání nové implementace rozhraní do typu**</span><span class="sxs-lookup"><span data-stu-id="7d954-125">❓ **REQUIRES JUDGMENT: Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="7d954-126">Jedná se o přijatelnou změnu, protože nepříznivě neovlivní stávající klienty.</span><span class="sxs-lookup"><span data-stu-id="7d954-126">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="7d954-127">Všechny změny typu musí fungovat v rámci hranic přijatelných změn, které jsou zde definovány, aby nová implementace zůstala přijatelná.</span><span class="sxs-lookup"><span data-stu-id="7d954-127">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="7d954-128">Při přidávání rozhraní, která přímo ovlivňují schopnost návrháře nebo serializátoru vytvořit kód nebo data, která nelze spotřebovat na nižší úroveň, je nezbytné extrémní opatrnost.</span><span class="sxs-lookup"><span data-stu-id="7d954-128">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="7d954-129">Příkladem je <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7d954-129">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="7d954-130">❓ **Vyžaduje rozhodnutí: Představujeme novou základní třídu.**</span><span class="sxs-lookup"><span data-stu-id="7d954-130">❓ **REQUIRES JUDGMENT: Introducing a new base class**</span></span>

  <span data-ttu-id="7d954-131">Typ lze začlenit do hierarchie mezi dvěma existujícími typy, pokud nezavádí žádné nové [abstraktní](../../csharp/language-reference/keywords/abstract.md) členy nebo nemění sémantiku nebo chování stávajících typů.</span><span class="sxs-lookup"><span data-stu-id="7d954-131">A type can be introduced into a hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="7d954-132">Například v .NET Framework 2,0 se <xref:System.Data.Common.DbConnection> třída stala novou základní třídou pro <xref:System.Data.SqlClient.SqlConnection>, která byla dříve odvozena přímo od <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="7d954-132">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="7d954-133">✔️ **povoleno: přesunutí typu z jednoho sestavení do druhého**</span><span class="sxs-lookup"><span data-stu-id="7d954-133">✔️ **ALLOWED: Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="7d954-134">*Původní* sestavení musí být označeno <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>, které odkazuje na nové sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d954-134">The *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="7d954-135">✔️ **povoleno: Změna typu [struktury](../../csharp/language-reference/builtin-types/struct.md) na typ `readonly struct`**</span><span class="sxs-lookup"><span data-stu-id="7d954-135">✔️ **ALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="7d954-136">Změna typu `readonly struct` na typ `struct` není povolená.</span><span class="sxs-lookup"><span data-stu-id="7d954-136">Changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="7d954-137">✔️ **povoleno: přidání [zapečetěného](../../csharp/language-reference/keywords/sealed.md) nebo [abstraktního](../../csharp/language-reference/keywords/abstract.md) klíčového slova do typu, pokud nejsou k *dispozici* žádné (veřejné nebo chráněné) konstruktory**</span><span class="sxs-lookup"><span data-stu-id="7d954-137">✔️ **ALLOWED: Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="7d954-138">✔️ **povoleno: rozšíření viditelnosti typu**</span><span class="sxs-lookup"><span data-stu-id="7d954-138">✔️ **ALLOWED: Expanding the visibility of a type**</span></span>

- <span data-ttu-id="7d954-139">❌ **zakázané: Změna oboru názvů nebo názvu typu**</span><span class="sxs-lookup"><span data-stu-id="7d954-139">❌ **DISALLOWED: Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="7d954-140">❌ **zakázané: přejmenování nebo odebrání veřejného typu**</span><span class="sxs-lookup"><span data-stu-id="7d954-140">❌ **DISALLOWED: Renaming or removing a public type**</span></span>

   <span data-ttu-id="7d954-141">Tím dojde k zalomení veškerého kódu, který používá přejmenovaný nebo odebraný typ.</span><span class="sxs-lookup"><span data-stu-id="7d954-141">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="7d954-142">❌ **zakázané: Změna základního typu výčtu**</span><span class="sxs-lookup"><span data-stu-id="7d954-142">❌ **DISALLOWED: Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="7d954-143">Toto je zásadní změna v době kompilace a chování a také binární zásadní změna, která může nastavit argumenty atributu jako neanalyzovatelné.</span><span class="sxs-lookup"><span data-stu-id="7d954-143">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="7d954-144">❌ **zakázané: zapečetění typu, který se dřív nezapečetěný**</span><span class="sxs-lookup"><span data-stu-id="7d954-144">❌ **DISALLOWED: Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="7d954-145">❌ **zakázané: Přidání rozhraní do sady základních typů rozhraní**</span><span class="sxs-lookup"><span data-stu-id="7d954-145">❌ **DISALLOWED: Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="7d954-146">Pokud rozhraní implementuje rozhraní, které dříve neimplementovalo, všechny typy, které implementují původní verzi rozhraní, jsou přerušeny.</span><span class="sxs-lookup"><span data-stu-id="7d954-146">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="7d954-147">❓ **Vyžaduje rozhodnutí: odebrání třídy ze sady základních tříd nebo rozhraní ze sady implementovaných rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="7d954-147">❓ **REQUIRES JUDGMENT: Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="7d954-148">Pravidlo pro odebrání rozhraní obsahuje jednu výjimku: můžete přidat implementaci rozhraní, které je odvozeno z odebraného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7d954-148">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="7d954-149">Můžete například odebrat <xref:System.IDisposable>, pokud typ nebo rozhraní nyní implementuje <xref:System.ComponentModel.IComponent>, které implementuje <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="7d954-149">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="7d954-150">❌ **zakázané: Změna typu `readonly struct` na typ [struktury](../../csharp/language-reference/builtin-types/struct.md)**</span><span class="sxs-lookup"><span data-stu-id="7d954-150">❌ **DISALLOWED: Changing a `readonly struct` type to a [struct](../../csharp/language-reference/builtin-types/struct.md) type**</span></span>

  <span data-ttu-id="7d954-151">Změna typu `struct` na typ `readonly struct` je povolena, ale.</span><span class="sxs-lookup"><span data-stu-id="7d954-151">The change of a `struct` type to a `readonly struct` type is allowed, however.</span></span>

- <span data-ttu-id="7d954-152">❌ **zakázané: Změna typu [struktury](../../csharp/language-reference/builtin-types/struct.md) na typ `ref struct` a naopak**</span><span class="sxs-lookup"><span data-stu-id="7d954-152">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="7d954-153">❌ **zakázané: zmenšení viditelnosti typu**</span><span class="sxs-lookup"><span data-stu-id="7d954-153">❌ **DISALLOWED: Reducing the visibility of a type**</span></span>

   <span data-ttu-id="7d954-154">Nicméně zvýšení viditelnosti typu je povoleno.</span><span class="sxs-lookup"><span data-stu-id="7d954-154">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="7d954-155">Členové</span><span class="sxs-lookup"><span data-stu-id="7d954-155">Members</span></span>

- <span data-ttu-id="7d954-156">✔️ **povoleno: rozšíření viditelnosti člena, který není [virtuální](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="7d954-156">✔️ **ALLOWED: Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="7d954-157">✔️ **povoleno: Přidání abstraktního člena do veřejného typu, který nemá žádné *přístupné* (veřejné nebo chráněné) konstruktory nebo je typ [zapečetěn](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="7d954-157">✔️ **ALLOWED: Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="7d954-158">Nicméně přidání abstraktního člena do typu, který má přístupné (veřejné nebo chráněné) konstruktory a není `sealed` není povoleno.</span><span class="sxs-lookup"><span data-stu-id="7d954-158">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="7d954-159">✔️ **povoleno: omezení viditelnosti [chráněného](../../csharp/language-reference/keywords/protected.md) člena, když typ nemá žádné přístupné (veřejné nebo chráněné) konstruktory nebo je typ [zapečetěn](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="7d954-159">✔️ **ALLOWED: Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="7d954-160">✔️ **povoleno: přesun člena do třídy vyšší v hierarchii, než je typ, ze kterého byl odebrán**</span><span class="sxs-lookup"><span data-stu-id="7d954-160">✔️ **ALLOWED: Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="7d954-161">✔️ **povoleno: Přidání nebo odebrání přepsání**</span><span class="sxs-lookup"><span data-stu-id="7d954-161">✔️ **ALLOWED: Adding or removing an override**</span></span>

  <span data-ttu-id="7d954-162">Představení přepsání může způsobit, že předchozí příjemci přeskočí přepsání při volání [základny](../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="7d954-162">Introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="7d954-163">✔️ **povoleno: Přidání konstruktoru do třídy spolu s konstruktorem bez parametrů, pokud třída předtím neměla žádné konstruktory**</span><span class="sxs-lookup"><span data-stu-id="7d954-163">✔️ **ALLOWED: Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="7d954-164">Nicméně přidání konstruktoru do třídy, která dříve neměla žádné konstruktory bez přidání konstruktoru *bez* parametrů, není povoleno.</span><span class="sxs-lookup"><span data-stu-id="7d954-164">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="7d954-165">✔️ **povoleno: Změna člena z [abstract](../../csharp/language-reference/keywords/abstract.md) na [Virtual](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="7d954-165">✔️ **ALLOWED: Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="7d954-166">✔️ **povoleno: Změna z `ref readonly` na `ref` návratovou hodnotu (s výjimkou virtuálních metod nebo rozhraní)**</span><span class="sxs-lookup"><span data-stu-id="7d954-166">✔️ **ALLOWED: Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="7d954-167">✔️ **povoleno: odebrání [jen pro čtení](../../csharp/language-reference/keywords/readonly.md) z pole, pokud statický typ pole není proměnlivý typ hodnoty**</span><span class="sxs-lookup"><span data-stu-id="7d954-167">✔️ **ALLOWED: Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="7d954-168">✔️ **povoleno: volání nové události, která nebyla dříve definována.**</span><span class="sxs-lookup"><span data-stu-id="7d954-168">✔️ **ALLOWED: Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="7d954-169">❓ **Vyžaduje rozhodnutí: Přidání nového pole instance do typu**</span><span class="sxs-lookup"><span data-stu-id="7d954-169">❓ **REQUIRES JUDGMENT: Adding a new instance field to a type**</span></span>

   <span data-ttu-id="7d954-170">Tato změna ovlivňuje serializaci.</span><span class="sxs-lookup"><span data-stu-id="7d954-170">This change impacts serialization.</span></span>

- <span data-ttu-id="7d954-171">❌ **zakázané: přejmenování nebo odebrání veřejného členu nebo parametru**</span><span class="sxs-lookup"><span data-stu-id="7d954-171">❌ **DISALLOWED: Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="7d954-172">Tím dojde k rozdělení veškerého kódu, který používá přejmenovaný nebo odebraný člen nebo parametr.</span><span class="sxs-lookup"><span data-stu-id="7d954-172">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="7d954-173">To zahrnuje odebrání nebo přejmenování metody getter nebo setter z vlastnosti a také přejmenování nebo odebrání členů výčtu.</span><span class="sxs-lookup"><span data-stu-id="7d954-173">This includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="7d954-174">❌ **zakázané: Přidání člena do rozhraní**</span><span class="sxs-lookup"><span data-stu-id="7d954-174">❌ **DISALLOWED: Adding a member to an interface**</span></span>

- <span data-ttu-id="7d954-175">❌ **zakázané: Změna hodnoty veřejné konstanty nebo člena výčtu**</span><span class="sxs-lookup"><span data-stu-id="7d954-175">❌ **DISALLOWED: Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="7d954-176">❌ **zakázané: Změna typu vlastnosti, pole, parametru nebo návratové hodnoty**</span><span class="sxs-lookup"><span data-stu-id="7d954-176">❌ **DISALLOWED: Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="7d954-177">❌ **zakázané: Přidání, odebrání nebo změna pořadí parametrů**</span><span class="sxs-lookup"><span data-stu-id="7d954-177">❌ **DISALLOWED: Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="7d954-178">❌ **zakázané: Přidání nebo odebrání klíčového slova [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) nebo [ref](../../csharp/language-reference/keywords/ref.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="7d954-178">❌ **DISALLOWED: Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="7d954-179">❌ **zakázané: Přejmenování parametru (včetně změny jeho velikosti)**</span><span class="sxs-lookup"><span data-stu-id="7d954-179">❌ **DISALLOWED: Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="7d954-180">To se považuje za porušení dvou důvodů:</span><span class="sxs-lookup"><span data-stu-id="7d954-180">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="7d954-181">Dojde k přerušení scénářů s pozdní vazbou, jako je funkce pozdní vazby [](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) v Visual Basic C#a dynamické v.</span><span class="sxs-lookup"><span data-stu-id="7d954-181">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="7d954-182">Pokud vývojáři používají [pojmenované argumenty](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments), dojde k přerušení [kompatibility zdrojů](categories.md#source-compatibility) .</span><span class="sxs-lookup"><span data-stu-id="7d954-182">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="7d954-183">❌ **zakázané: Změna ze `ref` návratové hodnoty na `ref readonly` návratovou hodnotu**</span><span class="sxs-lookup"><span data-stu-id="7d954-183">❌ **DISALLOWED: Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="7d954-184">❌️ **zakázané: Změna z `ref readonly` na `ref` návratovou hodnotu ve virtuální metodě nebo rozhraní**</span><span class="sxs-lookup"><span data-stu-id="7d954-184">❌️ **DISALLOWED: Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="7d954-185">❌ **zakázané: Přidání nebo odebrání [abstraktu](../../csharp/language-reference/keywords/abstract.md) ze člena**</span><span class="sxs-lookup"><span data-stu-id="7d954-185">❌ **DISALLOWED: Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="7d954-186">❌ **zakázané: odebrání klíčového slova [Virtual](../../csharp/language-reference/keywords/virtual.md) ze člena**</span><span class="sxs-lookup"><span data-stu-id="7d954-186">❌ **DISALLOWED: Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="7d954-187">I když se často nejedná o zásadní změnu, C# protože kompilátor chce vygenerovat instrukce [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) pro volání nevirtuálních metod (`callvirt` provádí kontrolu null, zatímco normální volání ne), toto chování není pro několik důvodů neproměnné:</span><span class="sxs-lookup"><span data-stu-id="7d954-187">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="7d954-188">C#není jediným jazykem, který cílí na .NET.</span><span class="sxs-lookup"><span data-stu-id="7d954-188">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="7d954-189">C# Kompilátor stále častěji snaží optimalizovat `callvirt` na normální volání, kdykoli je cílová metoda nevirtuální a pravděpodobně není null (například metoda, ke které se přistupoval prostřednictvím [operátoru rozšíření?. null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span><span class="sxs-lookup"><span data-stu-id="7d954-189">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="7d954-190">Vytvořením metody Virtual by kód příjemce často ukončil volání, které není prakticky.</span><span class="sxs-lookup"><span data-stu-id="7d954-190">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="7d954-191">❌ **zakázané: přidání klíčového slova [Virtual](../../csharp/language-reference/keywords/virtual.md) do člena**</span><span class="sxs-lookup"><span data-stu-id="7d954-191">❌ **DISALLOWED: Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="7d954-192">❌ **zakázané: vytváření abstraktního virtuálního člena**</span><span class="sxs-lookup"><span data-stu-id="7d954-192">❌ **DISALLOWED: Making a virtual member abstract**</span></span>

  <span data-ttu-id="7d954-193">[Virtuální člen](../../csharp/language-reference/keywords/virtual.md) poskytuje implementaci metody, kterou *lze* přepsat odvozenou třídou.</span><span class="sxs-lookup"><span data-stu-id="7d954-193">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="7d954-194">[Abstraktní člen](../../csharp/language-reference/keywords/abstract.md) neposkytuje žádnou implementaci a *musí být* přepsán.</span><span class="sxs-lookup"><span data-stu-id="7d954-194">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="7d954-195">❌ **zakázané: Přidání abstraktního člena k veřejnému typu, který má přístupné (veřejné nebo chráněné) konstruktory, které nejsou [zapečetěné](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="7d954-195">❌ **DISALLOWED: Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="7d954-196">❌ **zakázané: Přidání nebo odebrání klíčového slova [static](../../csharp/language-reference/keywords/static.md) ze člena**</span><span class="sxs-lookup"><span data-stu-id="7d954-196">❌ **DISALLOWED: Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="7d954-197">❌ **zakázané: Přidání přetížení, které vylučuje existující přetížení a definuje jiné chování.**</span><span class="sxs-lookup"><span data-stu-id="7d954-197">❌ **DISALLOWED: Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="7d954-198">Tím dojde k přerušení stávajících klientů vázaných na předchozí přetížení.</span><span class="sxs-lookup"><span data-stu-id="7d954-198">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="7d954-199">Například pokud má třída jedinou verzi metody, která přijímá <xref:System.UInt32>, existující příjemce se úspěšně připojí k tomuto přetížení při předávání hodnoty <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="7d954-199">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="7d954-200">Nicméně pokud přidáte přetížení, které přijímá <xref:System.Int32>, při rekompilování nebo použití pozdní vazby nyní kompilátor vytvoří vazbu k novému přetížení.</span><span class="sxs-lookup"><span data-stu-id="7d954-200">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="7d954-201">Pokud dojde k různým výsledkům chování, jedná se o zásadní změnu.</span><span class="sxs-lookup"><span data-stu-id="7d954-201">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="7d954-202">❌ **zakázané: Přidání konstruktoru do třídy, která dřív neměla žádný konstruktor bez nutnosti přidat konstruktor bez parametrů**</span><span class="sxs-lookup"><span data-stu-id="7d954-202">❌ **DISALLOWED: Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="7d954-203">❌️ **zakázané: přidání [ReadOnly](../../csharp/language-reference/keywords/readonly.md) do pole**</span><span class="sxs-lookup"><span data-stu-id="7d954-203">❌️ **DISALLOWED: Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="7d954-204">❌ **zakázané: zmenšení viditelnosti člena**</span><span class="sxs-lookup"><span data-stu-id="7d954-204">❌ **DISALLOWED: Reducing the visibility of a member**</span></span>

   <span data-ttu-id="7d954-205">To zahrnuje snížení viditelnosti [chráněného](../../csharp/language-reference/keywords/protected.md) člena, pokud jsou *přístupné* konstruktory (`public` nebo `protected`) a *typ není* [zapečetěný](../../csharp/language-reference/keywords/sealed.md).</span><span class="sxs-lookup"><span data-stu-id="7d954-205">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (`public` or `protected`) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="7d954-206">V takovém případě se omezení viditelnosti chráněného člena povoluje.</span><span class="sxs-lookup"><span data-stu-id="7d954-206">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="7d954-207">Zvýšení viditelnosti člena je povoleno.</span><span class="sxs-lookup"><span data-stu-id="7d954-207">Increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="7d954-208">❌ **zakázané: Změna typu člena**</span><span class="sxs-lookup"><span data-stu-id="7d954-208">❌ **DISALLOWED: Changing the type of a member**</span></span>

   <span data-ttu-id="7d954-209">Vrácenou hodnotu metody nebo typu pole nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="7d954-209">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="7d954-210">Například podpis metody, která vrací <xref:System.Object>, nelze změnit tak, aby vracela <xref:System.String>, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="7d954-210">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="7d954-211">❌ **zakázané: Přidání pole do struktury, která dřív neměla žádný stav**</span><span class="sxs-lookup"><span data-stu-id="7d954-211">❌ **DISALLOWED: Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="7d954-212">Pravidla pro jednoznačné přiřazení umožňují použití neinicializovaných proměnných, pokud typ proměnné je Bezstavová struktura.</span><span class="sxs-lookup"><span data-stu-id="7d954-212">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="7d954-213">Pokud je struktura nastavená jako stavová, může kód končit neinicializovanými daty.</span><span class="sxs-lookup"><span data-stu-id="7d954-213">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="7d954-214">To může být i poškození zdroje a binární změna.</span><span class="sxs-lookup"><span data-stu-id="7d954-214">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="7d954-215">❌ **zakázané: Vypálení existující události, když se ještě neaktivovala**</span><span class="sxs-lookup"><span data-stu-id="7d954-215">❌ **DISALLOWED: Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="7d954-216">Změny chování</span><span class="sxs-lookup"><span data-stu-id="7d954-216">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="7d954-217">Sestavení</span><span class="sxs-lookup"><span data-stu-id="7d954-217">Assemblies</span></span>

- <span data-ttu-id="7d954-218">✔️ **povoleno: sestavení přenositelného přenosného, pokud jsou stejné platformy stále podporovány**</span><span class="sxs-lookup"><span data-stu-id="7d954-218">✔️ **ALLOWED: Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="7d954-219">❌ **zakázané: Změna názvu sestavení**</span><span class="sxs-lookup"><span data-stu-id="7d954-219">❌ **DISALLOWED: Changing the name of an assembly**</span></span>
- <span data-ttu-id="7d954-220">❌ **zakázané: Změna veřejného klíče sestavení**</span><span class="sxs-lookup"><span data-stu-id="7d954-220">❌ **DISALLOWED: Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="7d954-221">Vlastnosti, pole, parametry a návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="7d954-221">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="7d954-222">✔️ **povoleno: Změna hodnoty vlastnosti, pole, návratové hodnoty nebo parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na více odvozený typ**</span><span class="sxs-lookup"><span data-stu-id="7d954-222">✔️ **ALLOWED: Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="7d954-223">Například metoda, která vrací typ <xref:System.Object> může vracet instanci <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="7d954-223">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="7d954-224">(Signatura metody se ale nemůže změnit.)</span><span class="sxs-lookup"><span data-stu-id="7d954-224">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="7d954-225">✔️ **povoleno: zvýšení rozsahu přípustných hodnot pro vlastnost nebo parametr, pokud člen není [virtuální](../../csharp/language-reference/keywords/virtual.md)**  .</span><span class="sxs-lookup"><span data-stu-id="7d954-225">✔️ **ALLOWED: Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="7d954-226">I když rozsah hodnot, které lze předat metodě nebo které mohou být vráceny členem, lze rozšířit, parametr nebo typ člena nemůže.</span><span class="sxs-lookup"><span data-stu-id="7d954-226">While the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="7d954-227">Například zatímco hodnoty předané metodě lze rozšířit z 0-124 na 0-255, typ parametru nemůže být změněn z <xref:System.Byte> na <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="7d954-227">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="7d954-228">❌ **zakázané: zvýšení rozsahu přípustných hodnot pro vlastnost nebo parametr, pokud je člen [virtuální](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="7d954-228">❌ **DISALLOWED: Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="7d954-229">Tato změna rozdělí existující přepsané členy, které nebudou správně fungovat pro rozšířený rozsah hodnot.</span><span class="sxs-lookup"><span data-stu-id="7d954-229">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="7d954-230">❌ **zakázané: zmenšení rozsahu přípustných hodnot pro vlastnost nebo parametr**</span><span class="sxs-lookup"><span data-stu-id="7d954-230">❌ **DISALLOWED: Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="7d954-231">❌ **zakázané: zvýšení rozsahu vrácených hodnot pro vlastnost, pole, návratovou hodnotu nebo [výstupní](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**</span><span class="sxs-lookup"><span data-stu-id="7d954-231">❌ **DISALLOWED: Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="7d954-232">❌ **zakázané: Změna vrácených hodnot pro vlastnost, pole, návratovou hodnotu metody nebo [výstupní](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**</span><span class="sxs-lookup"><span data-stu-id="7d954-232">❌ **DISALLOWED: Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="7d954-233">❌ **zakázané: Změna výchozí hodnoty vlastnosti, pole nebo parametru**</span><span class="sxs-lookup"><span data-stu-id="7d954-233">❌ **DISALLOWED: Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="7d954-234">❌ **zakázané: Změna přesnosti číselné návratové hodnoty**</span><span class="sxs-lookup"><span data-stu-id="7d954-234">❌ **DISALLOWED: Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="7d954-235">❓ **Vyžaduje rozhodnutí: Změna v analýze vstupu a vyvolání nových výjimek (i v případě, že se v dokumentaci nezadá chování při analýze).**</span><span class="sxs-lookup"><span data-stu-id="7d954-235">❓ **REQUIRES JUDGMENT: A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="7d954-236">Výjimky</span><span class="sxs-lookup"><span data-stu-id="7d954-236">Exceptions</span></span>

- <span data-ttu-id="7d954-237">✔️ **povoleno: vyvolání více odvozené výjimky, než je stávající výjimka**</span><span class="sxs-lookup"><span data-stu-id="7d954-237">✔️ **ALLOWED: Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="7d954-238">Vzhledem k tomu, že nová výjimka je podtřídou existující výjimky, pokračuje zpracování předchozí kódu zpracováním výjimky.</span><span class="sxs-lookup"><span data-stu-id="7d954-238">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="7d954-239">Například v .NET Framework 4 začaly metody vytváření a načítání jazykové verze vyvolávat <xref:System.Globalization.CultureNotFoundException> namísto <xref:System.ArgumentException>, pokud nebyla nalezena jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="7d954-239">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="7d954-240">Vzhledem k tomu, že <xref:System.Globalization.CultureNotFoundException> jsou odvozeny z <xref:System.ArgumentException>, jedná se o přijatelnou změnu.</span><span class="sxs-lookup"><span data-stu-id="7d954-240">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="7d954-241">✔️ **povoleno: byla aktivována konkrétnější výjimka než <xref:System.NotSupportedException>, <xref:System.NotImplementedException><xref:System.NullReferenceException>**</span><span class="sxs-lookup"><span data-stu-id="7d954-241">✔️ **ALLOWED: Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="7d954-242">✔️ **povoleno: probíhá vyvolání výjimky, která je považována za neodstranitelnou.**</span><span class="sxs-lookup"><span data-stu-id="7d954-242">✔️ **ALLOWED: Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="7d954-243">Neodstranitelné výjimky by neměly být zachyceny, ale místo toho by měly být zpracovány pomocí obslužné rutiny catch na vysoké úrovni.</span><span class="sxs-lookup"><span data-stu-id="7d954-243">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="7d954-244">Proto se neočekává, že uživatelé budou mít kód, který tyto explicitní výjimky zachytí.</span><span class="sxs-lookup"><span data-stu-id="7d954-244">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="7d954-245">Neobnovitelné výjimky jsou:</span><span class="sxs-lookup"><span data-stu-id="7d954-245">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="7d954-246">✔️ **povoleno: probíhá vyvolání nové výjimky v nové cestě kódu.**</span><span class="sxs-lookup"><span data-stu-id="7d954-246">✔️ **ALLOWED: Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="7d954-247">Výjimka se musí vztahovat jenom k nové cestě kódu, která se spustí s novými hodnotami parametrů nebo stavem a kterou nejde spustit pomocí stávajícího kódu, který cílí na předchozí verzi.</span><span class="sxs-lookup"><span data-stu-id="7d954-247">The exception must apply only to a new code-path that's executed with new parameter values or state and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="7d954-248">✔️ **povoleno: odebrání výjimky pro povolení robustnějšího chování nebo nových scénářů**</span><span class="sxs-lookup"><span data-stu-id="7d954-248">✔️ **ALLOWED: Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="7d954-249">Například `Divide` metoda, která dříve zpracovala pouze kladné hodnoty a vyvolala <xref:System.ArgumentOutOfRangeException> jinak může být změněna tak, aby podporovala záporné i kladné hodnoty bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="7d954-249">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="7d954-250">✔️ **povoleno: Změna textu chybové zprávy**</span><span class="sxs-lookup"><span data-stu-id="7d954-250">✔️ **ALLOWED: Changing the text of an error message**</span></span>

  <span data-ttu-id="7d954-251">Vývojáři by neměli spoléhat na text chybových zpráv, které se také mění v závislosti na jazykové verzi uživatele.</span><span class="sxs-lookup"><span data-stu-id="7d954-251">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="7d954-252">❌ **zakázané: vyvolává se výjimka v jakémkoli jiném případě, který není uvedený výše.**</span><span class="sxs-lookup"><span data-stu-id="7d954-252">❌ **DISALLOWED: Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="7d954-253">❌ **zakázané: odebrání výjimky v jakémkoli jiném případě, který není uvedený výše**</span><span class="sxs-lookup"><span data-stu-id="7d954-253">❌ **DISALLOWED: Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="7d954-254">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d954-254">Attributes</span></span>

- <span data-ttu-id="7d954-255">✔️ **povoleno: Změna hodnoty atributu, který není *možné* pozorovat**</span><span class="sxs-lookup"><span data-stu-id="7d954-255">✔️ **ALLOWED: Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="7d954-256">❌ **zakázané: Změna hodnoty atributu, který *je* možné pozorovat**</span><span class="sxs-lookup"><span data-stu-id="7d954-256">❌ **DISALLOWED: Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="7d954-257">❓ **Vyžaduje rozhodnutí: odebrání atributu**</span><span class="sxs-lookup"><span data-stu-id="7d954-257">❓ **REQUIRES JUDGMENT: Removing an attribute**</span></span>

  <span data-ttu-id="7d954-258">Ve většině případů je odebrání atributu (například <xref:System.NonSerializedAttribute>) zásadní změnou.</span><span class="sxs-lookup"><span data-stu-id="7d954-258">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="7d954-259">Podpora platformy</span><span class="sxs-lookup"><span data-stu-id="7d954-259">Platform support</span></span>

- <span data-ttu-id="7d954-260">✔️ **povoleno: podpora operace na platformě, která nebyla dříve podporována**</span><span class="sxs-lookup"><span data-stu-id="7d954-260">✔️ **ALLOWED: Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="7d954-261">❌ **Nepovoleno: Nepodporováno nebo nyní nevyžaduje konkrétní aktualizaci Service Pack pro operaci, která byla dříve podporovaná na platformě.**</span><span class="sxs-lookup"><span data-stu-id="7d954-261">❌ **DISALLOWED: Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="7d954-262">Změny interní implementace</span><span class="sxs-lookup"><span data-stu-id="7d954-262">Internal implementation changes</span></span>

- <span data-ttu-id="7d954-263">❓ **Vyžaduje rozhodnutí: Změna oblasti povrchu interního typu**</span><span class="sxs-lookup"><span data-stu-id="7d954-263">❓ **REQUIRES JUDGMENT: Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="7d954-264">Tyto změny jsou obecně povoleny, i když přeruší soukromý odraz.</span><span class="sxs-lookup"><span data-stu-id="7d954-264">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="7d954-265">V některých případech, kde jsou oblíbené knihovny třetích stran nebo velký počet vývojářů závislé na interních rozhraních API, nemusí být tyto změny povolené.</span><span class="sxs-lookup"><span data-stu-id="7d954-265">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="7d954-266">❓ **Vyžaduje rozhodnutí: Změna interní implementace členu.**</span><span class="sxs-lookup"><span data-stu-id="7d954-266">❓ **REQUIRES JUDGMENT: Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="7d954-267">Tyto změny jsou obecně povoleny, i když přeruší soukromý odraz.</span><span class="sxs-lookup"><span data-stu-id="7d954-267">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="7d954-268">V některých případech, kde kód zákazníka často závisí na soukromé reflexi nebo kde změna zavádí nezamýšlené vedlejší účinky, nemusí být tyto změny povoleny.</span><span class="sxs-lookup"><span data-stu-id="7d954-268">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="7d954-269">✔️ **povoleno: zlepšení výkonu operace**</span><span class="sxs-lookup"><span data-stu-id="7d954-269">✔️ **ALLOWED: Improving the performance of an operation**</span></span>

   <span data-ttu-id="7d954-270">Možnost upravit výkon operace je zásadní, ale tyto změny mohou přerušit kód, který spoléhá na aktuální rychlost operace.</span><span class="sxs-lookup"><span data-stu-id="7d954-270">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="7d954-271">To platí zejména pro kód, který závisí na časování asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="7d954-271">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="7d954-272">Změna výkonu by neměla mít žádný vliv na jiné chování rozhraní API. v opačném případě bude změna zálomena.</span><span class="sxs-lookup"><span data-stu-id="7d954-272">The performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="7d954-273">✔️ **povoleno: nepřímo (a často nepříznivě) měnit výkon operace**</span><span class="sxs-lookup"><span data-stu-id="7d954-273">✔️ **ALLOWED: Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="7d954-274">Pokud se změna nedělí z nějakého jiného důvodu jako porušení, je to přijatelné.</span><span class="sxs-lookup"><span data-stu-id="7d954-274">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="7d954-275">Často je potřeba provést akce, které mohou zahrnovat dodatečné operace nebo které přidávají nové funkce.</span><span class="sxs-lookup"><span data-stu-id="7d954-275">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="7d954-276">To bude téměř vždy mít vliv na výkon, ale může být nezbytné, aby rozhraní API fungovalo podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="7d954-276">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="7d954-277">❌ **zakázané: Změna synchronního rozhraní API na asynchronní (a naopak)**</span><span class="sxs-lookup"><span data-stu-id="7d954-277">❌ **DISALLOWED: Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="7d954-278">Změny kódu</span><span class="sxs-lookup"><span data-stu-id="7d954-278">Code changes</span></span>

- <span data-ttu-id="7d954-279">✔️ **povoleno: přidání [parametrů](../../csharp/language-reference/keywords/params.md) do parametru**</span><span class="sxs-lookup"><span data-stu-id="7d954-279">✔️ **ALLOWED: Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="7d954-280">❌ **zakázané: Změna [struktury](../../csharp/language-reference/builtin-types/struct.md) na [třídu](../../csharp/language-reference/keywords/class.md) a naopak**</span><span class="sxs-lookup"><span data-stu-id="7d954-280">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="7d954-281">❌ **zakázané: přidání klíčového slova [checked](../../csharp/language-reference/keywords/virtual.md) do bloku kódu**</span><span class="sxs-lookup"><span data-stu-id="7d954-281">❌ **DISALLOWED: Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="7d954-282">Tato změna může způsobit, že kód, který dřív provedl k vyvolání <xref:System.OverflowException> a je nepřijatelný.</span><span class="sxs-lookup"><span data-stu-id="7d954-282">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="7d954-283">❌ **zakázané: odebírání [parametrů](../../csharp/language-reference/keywords/params.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="7d954-283">❌ **DISALLOWED: Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="7d954-284">❌ **zakázané: Změna pořadí, ve kterém se události aktivují**</span><span class="sxs-lookup"><span data-stu-id="7d954-284">❌ **DISALLOWED: Changing the order in which events are fired**</span></span>

  <span data-ttu-id="7d954-285">Vývojáři mohou rozumně očekávat, že události budou aktivovány ve stejném pořadí a kód pro vývojáře často závisí na pořadí, ve kterém jsou události vyvolány.</span><span class="sxs-lookup"><span data-stu-id="7d954-285">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="7d954-286">❌ **zakázané: odebrání vyvolání události na dané akci**</span><span class="sxs-lookup"><span data-stu-id="7d954-286">❌ **DISALLOWED: Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="7d954-287">❌ **zakázané: Změna počtu volání daných událostí**</span><span class="sxs-lookup"><span data-stu-id="7d954-287">❌ **DISALLOWED: Changing the number of times given events are called**</span></span>

- <span data-ttu-id="7d954-288">❌ **zakázané: přidání <xref:System.FlagsAttribute> do výčtového typu**</span><span class="sxs-lookup"><span data-stu-id="7d954-288">❌ **DISALLOWED: Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>

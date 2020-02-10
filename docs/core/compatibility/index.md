---
title: Typy přerušujících změn
description: Přečtěte si, jak se .NET Core pokusí zachovat kompatibilitu pro vývojáře napříč verzemi .NET a jaký druh změny se považuje za zásadní změnu.
ms.date: 06/10/2019
ms.openlocfilehash: 1c5790e39754b91aacbde9e87ed99f9dcc36ce9f
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092977"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="337c5-103">Změny ovlivňující kompatibilitu</span><span class="sxs-lookup"><span data-stu-id="337c5-103">Changes that affect compatibility</span></span>

<span data-ttu-id="337c5-104">V průběhu své historie se .NET pokusilo udržet vysokou úroveň kompatibility z verze na verzi a v různých charakterech rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="337c5-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="337c5-105">To platí i pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="337c5-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="337c5-106">I když .NET Core se dá považovat za novou technologii, která je nezávislá na .NET Framework, dva hlavní faktory omezují schopnost .NET Core odchýlit se od .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="337c5-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="337c5-107">Velký počet vývojářů byl buď původně vyvinutý, nebo pokračoval v vývoji .NET Frameworkch aplikací.</span><span class="sxs-lookup"><span data-stu-id="337c5-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="337c5-108">Očekávají konzistentní chování napříč implementacemi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="337c5-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="337c5-109">Projekty knihovny .NET Standard umožňují vývojářům vytvářet knihovny, které cílí na společná rozhraní API sdílená pomocí .NET Core a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="337c5-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="337c5-110">Vývojáři očekávají, že se knihovna používaná v aplikaci .NET Core musí chovat stejně jako stejná knihovna, jakou používá aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="337c5-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="337c5-111">Společně s kompatibilitou mezi implementacemi .NET očekávají vývojáři vysokou úroveň kompatibility napříč verzemi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="337c5-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="337c5-112">Konkrétně kód napsaný pro starší verzi rozhraní .NET Core by měl běžet plynule v novější verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="337c5-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="337c5-113">Mnoho vývojářů předpokládá, že nová rozhraní API nalezená v nově vydaných verzích rozhraní .NET Core by měla být také kompatibilní s předběžnými verzemi, ve kterých byla tato rozhraní API zavedena.</span><span class="sxs-lookup"><span data-stu-id="337c5-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="337c5-114">Tento článek popisuje kategorie změn kompatibility (nebo zásadní změny) a způsob, jakým tým .NET vyhodnocuje změny v každé z těchto kategorií.</span><span class="sxs-lookup"><span data-stu-id="337c5-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="337c5-115">Porozumění způsobu, jakým tým .NET přistupuje k možným nepřípadným změnám, je zvláště užitečné pro vývojáře, kteří otevřou žádosti o přijetí změn v úložišti GitHubu [a modulu runtime](https://github.com/dotnet/runtime) , které upravují chování existujících rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="337c5-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests in the [dotnet/runtime](https://github.com/dotnet/runtime) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="337c5-116">Definici kategorií kompatibility, jako je binární kompatibilita a zpětná kompatibilita, najdete v tématu [přerušující kategorie změn](categories.md).</span><span class="sxs-lookup"><span data-stu-id="337c5-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="337c5-117">Následující části popisují kategorie změn provedených v rozhraních API .NET Core a jejich dopad na kompatibilitu aplikací.</span><span class="sxs-lookup"><span data-stu-id="337c5-117">The following sections describe the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="337c5-118">Změny jsou buď povolené ✔️, nepovolené ❌, nebo vyžadují rozhodnutí a hodnocení, jak předvídatelné, zjevné a konzistentní předchozí chování byly ❓.</span><span class="sxs-lookup"><span data-stu-id="337c5-118">Changes are either allowed ✔️, disallowed ❌, or require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was ❓.</span></span>

> [!NOTE]
> <span data-ttu-id="337c5-119">Kromě toho, že slouží jako vodítko, jak jsou vyhodnocovány změny knihoven .NET Core, mohou vývojáři knihovny použít také k vyhodnocení změn ve svých knihovnách, které cílí na více implementací a verzí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="337c5-119">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="337c5-120">Úpravy veřejné smlouvy</span><span class="sxs-lookup"><span data-stu-id="337c5-120">Modifications to the public contract</span></span>

<span data-ttu-id="337c5-121">Změny v této kategorii upravují oblast veřejného povrchu typu.</span><span class="sxs-lookup"><span data-stu-id="337c5-121">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="337c5-122">Většina změn v této kategorii není povolená, protože narušují *zpětnou kompatibilitu* (schopnost aplikace, která byla vyvinutá pomocí předchozí verze rozhraní API, aby se spustila bez překompilace na novější verzi).</span><span class="sxs-lookup"><span data-stu-id="337c5-122">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="337c5-123">Typy</span><span class="sxs-lookup"><span data-stu-id="337c5-123">Types</span></span>

- <span data-ttu-id="337c5-124">✔️ **povoleno: odebrání implementace rozhraní z typu, když je rozhraní již implementováno pomocí základního typu**</span><span class="sxs-lookup"><span data-stu-id="337c5-124">✔️ **ALLOWED: Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="337c5-125">❓ **Vyžaduje rozhodnutí: Přidání nové implementace rozhraní do typu**</span><span class="sxs-lookup"><span data-stu-id="337c5-125">❓ **REQUIRES JUDGMENT: Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="337c5-126">Jedná se o přijatelnou změnu, protože nepříznivě neovlivní stávající klienty.</span><span class="sxs-lookup"><span data-stu-id="337c5-126">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="337c5-127">Všechny změny typu musí fungovat v rámci hranic přijatelných změn, které jsou zde definovány, aby nová implementace zůstala přijatelná.</span><span class="sxs-lookup"><span data-stu-id="337c5-127">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="337c5-128">Při přidávání rozhraní, která přímo ovlivňují schopnost návrháře nebo serializátoru vytvořit kód nebo data, která nelze spotřebovat na nižší úroveň, je nezbytné extrémní opatrnost.</span><span class="sxs-lookup"><span data-stu-id="337c5-128">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="337c5-129">Příkladem je <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="337c5-129">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="337c5-130">❓ **Vyžaduje rozhodnutí: Představujeme novou základní třídu.**</span><span class="sxs-lookup"><span data-stu-id="337c5-130">❓ **REQUIRES JUDGMENT: Introducing a new base class**</span></span>

  <span data-ttu-id="337c5-131">Typ lze začlenit do hierarchie mezi dvěma existujícími typy, pokud nezavádí žádné nové [abstraktní](../../csharp/language-reference/keywords/abstract.md) členy nebo nemění sémantiku nebo chování stávajících typů.</span><span class="sxs-lookup"><span data-stu-id="337c5-131">A type can be introduced into a hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="337c5-132">Například v .NET Framework 2,0 se <xref:System.Data.Common.DbConnection> třída stala novou základní třídou pro <xref:System.Data.SqlClient.SqlConnection>, která byla dříve odvozena přímo od <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="337c5-132">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="337c5-133">✔️ **povoleno: přesunutí typu z jednoho sestavení do druhého**</span><span class="sxs-lookup"><span data-stu-id="337c5-133">✔️ **ALLOWED: Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="337c5-134">*Původní* sestavení musí být označeno <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>, které odkazuje na nové sestavení.</span><span class="sxs-lookup"><span data-stu-id="337c5-134">The *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="337c5-135">✔️ **povoleno: Změna typu [struktury](../../csharp/language-reference/keywords/struct.md) na typ `readonly struct`**</span><span class="sxs-lookup"><span data-stu-id="337c5-135">✔️ **ALLOWED: Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="337c5-136">Změna typu `readonly struct` na typ `struct` není povolená.</span><span class="sxs-lookup"><span data-stu-id="337c5-136">Changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="337c5-137">✔️ **povoleno: přidání [zapečetěného](../../csharp/language-reference/keywords/sealed.md) nebo [abstraktního](../../csharp/language-reference/keywords/abstract.md) klíčového slova do typu, pokud nejsou k *dispozici* žádné (veřejné nebo chráněné) konstruktory**</span><span class="sxs-lookup"><span data-stu-id="337c5-137">✔️ **ALLOWED: Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="337c5-138">✔️ **povoleno: rozšíření viditelnosti typu**</span><span class="sxs-lookup"><span data-stu-id="337c5-138">✔️ **ALLOWED: Expanding the visibility of a type**</span></span>

- <span data-ttu-id="337c5-139">❌ **zakázané: Změna oboru názvů nebo názvu typu**</span><span class="sxs-lookup"><span data-stu-id="337c5-139">❌ **DISALLOWED: Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="337c5-140">❌ **zakázané: přejmenování nebo odebrání veřejného typu**</span><span class="sxs-lookup"><span data-stu-id="337c5-140">❌ **DISALLOWED: Renaming or removing a public type**</span></span>

   <span data-ttu-id="337c5-141">Tím dojde k zalomení veškerého kódu, který používá přejmenovaný nebo odebraný typ.</span><span class="sxs-lookup"><span data-stu-id="337c5-141">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="337c5-142">❌ **zakázané: Změna základního typu výčtu**</span><span class="sxs-lookup"><span data-stu-id="337c5-142">❌ **DISALLOWED: Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="337c5-143">Toto je zásadní změna v době kompilace a chování a také binární zásadní změna, která může nastavit argumenty atributu jako neanalyzovatelné.</span><span class="sxs-lookup"><span data-stu-id="337c5-143">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="337c5-144">❌ **zakázané: zapečetění typu, který se dřív nezapečetěný**</span><span class="sxs-lookup"><span data-stu-id="337c5-144">❌ **DISALLOWED: Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="337c5-145">❌ **zakázané: Přidání rozhraní do sady základních typů rozhraní**</span><span class="sxs-lookup"><span data-stu-id="337c5-145">❌ **DISALLOWED: Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="337c5-146">Pokud rozhraní implementuje rozhraní, které dříve neimplementovalo, všechny typy, které implementují původní verzi rozhraní, jsou přerušeny.</span><span class="sxs-lookup"><span data-stu-id="337c5-146">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="337c5-147">❓ **Vyžaduje rozhodnutí: odebrání třídy ze sady základních tříd nebo rozhraní ze sady implementovaných rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="337c5-147">❓ **REQUIRES JUDGMENT: Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="337c5-148">Pravidlo pro odebrání rozhraní obsahuje jednu výjimku: můžete přidat implementaci rozhraní, které je odvozeno z odebraného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="337c5-148">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="337c5-149">Můžete například odebrat <xref:System.IDisposable>, pokud typ nebo rozhraní nyní implementuje <xref:System.ComponentModel.IComponent>, které implementuje <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="337c5-149">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="337c5-150">❌ **zakázané: Změna typu `readonly struct` na typ [struktury](../../csharp/language-reference/keywords/struct.md)**</span><span class="sxs-lookup"><span data-stu-id="337c5-150">❌ **DISALLOWED: Changing a `readonly struct` type to a [struct](../../csharp/language-reference/keywords/struct.md) type**</span></span>

  <span data-ttu-id="337c5-151">Změna typu `struct` na typ `readonly struct` je povolena, ale.</span><span class="sxs-lookup"><span data-stu-id="337c5-151">The change of a `struct` type to a `readonly struct` type is allowed, however.</span></span>

- <span data-ttu-id="337c5-152">❌ **zakázané: Změna typu [struktury](../../csharp/language-reference/keywords/struct.md) na typ `ref struct` a naopak**</span><span class="sxs-lookup"><span data-stu-id="337c5-152">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="337c5-153">❌ **zakázané: zmenšení viditelnosti typu**</span><span class="sxs-lookup"><span data-stu-id="337c5-153">❌ **DISALLOWED: Reducing the visibility of a type**</span></span>

   <span data-ttu-id="337c5-154">Nicméně zvýšení viditelnosti typu je povoleno.</span><span class="sxs-lookup"><span data-stu-id="337c5-154">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="337c5-155">Členové</span><span class="sxs-lookup"><span data-stu-id="337c5-155">Members</span></span>

- <span data-ttu-id="337c5-156">✔️ **povoleno: rozšíření viditelnosti člena, který není [virtuální](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="337c5-156">✔️ **ALLOWED: Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="337c5-157">✔️ **povoleno: Přidání abstraktního člena do veřejného typu, který nemá žádné *přístupné* (veřejné nebo chráněné) konstruktory nebo je typ [zapečetěn](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="337c5-157">✔️ **ALLOWED: Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="337c5-158">Nicméně přidání abstraktního člena do typu, který má přístupné (veřejné nebo chráněné) konstruktory a není `sealed` není povoleno.</span><span class="sxs-lookup"><span data-stu-id="337c5-158">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="337c5-159">✔️ **povoleno: omezení viditelnosti [chráněného](../../csharp/language-reference/keywords/protected.md) člena, když typ nemá žádné přístupné (veřejné nebo chráněné) konstruktory nebo je typ [zapečetěn](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="337c5-159">✔️ **ALLOWED: Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="337c5-160">✔️ **povoleno: přesun člena do třídy vyšší v hierarchii, než je typ, ze kterého byl odebrán**</span><span class="sxs-lookup"><span data-stu-id="337c5-160">✔️ **ALLOWED: Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="337c5-161">✔️ **povoleno: Přidání nebo odebrání přepsání**</span><span class="sxs-lookup"><span data-stu-id="337c5-161">✔️ **ALLOWED: Adding or removing an override**</span></span>

  <span data-ttu-id="337c5-162">Představení přepsání může způsobit, že předchozí příjemci přeskočí přepsání při volání [základny](../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="337c5-162">Introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="337c5-163">✔️ **povoleno: Přidání konstruktoru do třídy spolu s konstruktorem bez parametrů, pokud třída předtím neměla žádné konstruktory**</span><span class="sxs-lookup"><span data-stu-id="337c5-163">✔️ **ALLOWED: Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="337c5-164">Nicméně přidání konstruktoru do třídy, která dříve neměla žádné konstruktory bez přidání konstruktoru *bez* parametrů, není povoleno.</span><span class="sxs-lookup"><span data-stu-id="337c5-164">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="337c5-165">✔️ **povoleno: Změna člena z [abstract](../../csharp/language-reference/keywords/abstract.md) na [Virtual](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="337c5-165">✔️ **ALLOWED: Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="337c5-166">✔️ **povoleno: Změna z `ref readonly` na `ref` návratovou hodnotu (s výjimkou virtuálních metod nebo rozhraní)**</span><span class="sxs-lookup"><span data-stu-id="337c5-166">✔️ **ALLOWED: Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="337c5-167">✔️ **povoleno: odebrání [jen pro čtení](../../csharp/language-reference/keywords/readonly.md) z pole, pokud statický typ pole není proměnlivý typ hodnoty**</span><span class="sxs-lookup"><span data-stu-id="337c5-167">✔️ **ALLOWED: Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="337c5-168">✔️ **povoleno: volání nové události, která nebyla dříve definována.**</span><span class="sxs-lookup"><span data-stu-id="337c5-168">✔️ **ALLOWED: Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="337c5-169">❓ **Vyžaduje rozhodnutí: Přidání nového pole instance do typu**</span><span class="sxs-lookup"><span data-stu-id="337c5-169">❓ **REQUIRES JUDGMENT: Adding a new instance field to a type**</span></span>

   <span data-ttu-id="337c5-170">Tato změna ovlivňuje serializaci.</span><span class="sxs-lookup"><span data-stu-id="337c5-170">This change impacts serialization.</span></span>

- <span data-ttu-id="337c5-171">❌ **zakázané: přejmenování nebo odebrání veřejného členu nebo parametru**</span><span class="sxs-lookup"><span data-stu-id="337c5-171">❌ **DISALLOWED: Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="337c5-172">Tím dojde k rozdělení veškerého kódu, který používá přejmenovaný nebo odebraný člen nebo parametr.</span><span class="sxs-lookup"><span data-stu-id="337c5-172">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="337c5-173">To zahrnuje odebrání nebo přejmenování metody getter nebo setter z vlastnosti a také přejmenování nebo odebrání členů výčtu.</span><span class="sxs-lookup"><span data-stu-id="337c5-173">This includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="337c5-174">❌ **zakázané: Přidání člena do rozhraní**</span><span class="sxs-lookup"><span data-stu-id="337c5-174">❌ **DISALLOWED: Adding a member to an interface**</span></span>

- <span data-ttu-id="337c5-175">❌ **zakázané: Změna hodnoty veřejné konstanty nebo člena výčtu**</span><span class="sxs-lookup"><span data-stu-id="337c5-175">❌ **DISALLOWED: Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="337c5-176">❌ **zakázané: Změna typu vlastnosti, pole, parametru nebo návratové hodnoty**</span><span class="sxs-lookup"><span data-stu-id="337c5-176">❌ **DISALLOWED: Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="337c5-177">❌ **zakázané: Přidání, odebrání nebo změna pořadí parametrů**</span><span class="sxs-lookup"><span data-stu-id="337c5-177">❌ **DISALLOWED: Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="337c5-178">❌ **zakázané: Přidání nebo odebrání klíčového slova [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) nebo [ref](../../csharp/language-reference/keywords/ref.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="337c5-178">❌ **DISALLOWED: Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="337c5-179">❌ **zakázané: Přejmenování parametru (včetně změny jeho velikosti)**</span><span class="sxs-lookup"><span data-stu-id="337c5-179">❌ **DISALLOWED: Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="337c5-180">To se považuje za porušení dvou důvodů:</span><span class="sxs-lookup"><span data-stu-id="337c5-180">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="337c5-181">Dojde k přerušení scénářů s pozdní vazbou, jako je funkce pozdní vazby [](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) v Visual Basic C#a dynamické v.</span><span class="sxs-lookup"><span data-stu-id="337c5-181">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="337c5-182">Pokud vývojáři používají [pojmenované argumenty](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments), dojde k přerušení [kompatibility zdrojů](categories.md#source-compatibility) .</span><span class="sxs-lookup"><span data-stu-id="337c5-182">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="337c5-183">❌ **zakázané: Změna ze `ref` návratové hodnoty na `ref readonly` návratovou hodnotu**</span><span class="sxs-lookup"><span data-stu-id="337c5-183">❌ **DISALLOWED: Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="337c5-184">❌️ **zakázané: Změna z `ref readonly` na `ref` návratovou hodnotu ve virtuální metodě nebo rozhraní**</span><span class="sxs-lookup"><span data-stu-id="337c5-184">❌️ **DISALLOWED: Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="337c5-185">❌ **zakázané: Přidání nebo odebrání [abstraktu](../../csharp/language-reference/keywords/abstract.md) ze člena**</span><span class="sxs-lookup"><span data-stu-id="337c5-185">❌ **DISALLOWED: Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="337c5-186">❌ **zakázané: odebrání klíčového slova [Virtual](../../csharp/language-reference/keywords/virtual.md) ze člena**</span><span class="sxs-lookup"><span data-stu-id="337c5-186">❌ **DISALLOWED: Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="337c5-187">I když se často nejedná o zásadní změnu, C# protože kompilátor chce vygenerovat instrukce [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) pro volání nevirtuálních metod (`callvirt` provádí kontrolu null, zatímco normální volání ne), toto chování není pro několik důvodů neproměnné:</span><span class="sxs-lookup"><span data-stu-id="337c5-187">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="337c5-188">C#není jediným jazykem, který cílí na .NET.</span><span class="sxs-lookup"><span data-stu-id="337c5-188">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="337c5-189">C# Kompilátor stále častěji snaží optimalizovat `callvirt` na normální volání, kdykoli je cílová metoda nevirtuální a pravděpodobně není null (například metoda, ke které se přistupoval prostřednictvím [operátoru rozšíření?. null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span><span class="sxs-lookup"><span data-stu-id="337c5-189">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="337c5-190">Vytvořením metody Virtual by kód příjemce často ukončil volání, které není prakticky.</span><span class="sxs-lookup"><span data-stu-id="337c5-190">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="337c5-191">❌ **zakázané: přidání klíčového slova [Virtual](../../csharp/language-reference/keywords/virtual.md) do člena**</span><span class="sxs-lookup"><span data-stu-id="337c5-191">❌ **DISALLOWED: Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="337c5-192">❌ **zakázané: vytváření abstraktního virtuálního člena**</span><span class="sxs-lookup"><span data-stu-id="337c5-192">❌ **DISALLOWED: Making a virtual member abstract**</span></span>

  <span data-ttu-id="337c5-193">[Virtuální člen](../../csharp/language-reference/keywords/virtual.md) poskytuje implementaci metody, kterou *lze* přepsat odvozenou třídou.</span><span class="sxs-lookup"><span data-stu-id="337c5-193">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="337c5-194">[Abstraktní člen](../../csharp/language-reference/keywords/abstract.md) neposkytuje žádnou implementaci a *musí být* přepsán.</span><span class="sxs-lookup"><span data-stu-id="337c5-194">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="337c5-195">❌ **zakázané: Přidání abstraktního člena k veřejnému typu, který má přístupné (veřejné nebo chráněné) konstruktory, které nejsou [zapečetěné](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="337c5-195">❌ **DISALLOWED: Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="337c5-196">❌ **zakázané: Přidání nebo odebrání klíčového slova [static](../../csharp/language-reference/keywords/static.md) ze člena**</span><span class="sxs-lookup"><span data-stu-id="337c5-196">❌ **DISALLOWED: Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="337c5-197">❌ **zakázané: Přidání přetížení, které vylučuje existující přetížení a definuje jiné chování.**</span><span class="sxs-lookup"><span data-stu-id="337c5-197">❌ **DISALLOWED: Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="337c5-198">Tím dojde k přerušení stávajících klientů vázaných na předchozí přetížení.</span><span class="sxs-lookup"><span data-stu-id="337c5-198">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="337c5-199">Například pokud má třída jedinou verzi metody, která přijímá <xref:System.UInt32>, existující příjemce se úspěšně připojí k tomuto přetížení při předávání hodnoty <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="337c5-199">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="337c5-200">Nicméně pokud přidáte přetížení, které přijímá <xref:System.Int32>, při rekompilování nebo použití pozdní vazby nyní kompilátor vytvoří vazbu k novému přetížení.</span><span class="sxs-lookup"><span data-stu-id="337c5-200">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="337c5-201">Pokud dojde k různým výsledkům chování, jedná se o zásadní změnu.</span><span class="sxs-lookup"><span data-stu-id="337c5-201">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="337c5-202">❌ **zakázané: Přidání konstruktoru do třídy, která dřív neměla žádný konstruktor bez nutnosti přidat konstruktor bez parametrů**</span><span class="sxs-lookup"><span data-stu-id="337c5-202">❌ **DISALLOWED: Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="337c5-203">❌️ **zakázané: přidání [ReadOnly](../../csharp/language-reference/keywords/readonly.md) do pole**</span><span class="sxs-lookup"><span data-stu-id="337c5-203">❌️ **DISALLOWED: Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="337c5-204">❌ **zakázané: zmenšení viditelnosti člena**</span><span class="sxs-lookup"><span data-stu-id="337c5-204">❌ **DISALLOWED: Reducing the visibility of a member**</span></span>

   <span data-ttu-id="337c5-205">To zahrnuje snížení viditelnosti [chráněného](../../csharp/language-reference/keywords/protected.md) člena, pokud jsou *přístupné* konstruktory (`public` nebo `protected`) a *typ není* [zapečetěný](../../csharp/language-reference/keywords/sealed.md).</span><span class="sxs-lookup"><span data-stu-id="337c5-205">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (`public` or `protected`) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="337c5-206">V takovém případě se omezení viditelnosti chráněného člena povoluje.</span><span class="sxs-lookup"><span data-stu-id="337c5-206">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="337c5-207">Zvýšení viditelnosti člena je povoleno.</span><span class="sxs-lookup"><span data-stu-id="337c5-207">Increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="337c5-208">❌ **zakázané: Změna typu člena**</span><span class="sxs-lookup"><span data-stu-id="337c5-208">❌ **DISALLOWED: Changing the type of a member**</span></span>

   <span data-ttu-id="337c5-209">Vrácenou hodnotu metody nebo typu pole nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="337c5-209">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="337c5-210">Například podpis metody, která vrací <xref:System.Object>, nelze změnit tak, aby vracela <xref:System.String>, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="337c5-210">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="337c5-211">❌ **zakázané: Přidání pole do struktury, která dřív neměla žádný stav**</span><span class="sxs-lookup"><span data-stu-id="337c5-211">❌ **DISALLOWED: Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="337c5-212">Pravidla pro jednoznačné přiřazení umožňují použití neinicializovaných proměnných, pokud typ proměnné je Bezstavová struktura.</span><span class="sxs-lookup"><span data-stu-id="337c5-212">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="337c5-213">Pokud je struktura nastavená jako stavová, může kód končit neinicializovanými daty.</span><span class="sxs-lookup"><span data-stu-id="337c5-213">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="337c5-214">To může být i poškození zdroje a binární změna.</span><span class="sxs-lookup"><span data-stu-id="337c5-214">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="337c5-215">❌ **zakázané: Vypálení existující události, když se ještě neaktivovala**</span><span class="sxs-lookup"><span data-stu-id="337c5-215">❌ **DISALLOWED: Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="337c5-216">Změny chování</span><span class="sxs-lookup"><span data-stu-id="337c5-216">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="337c5-217">Sestavení</span><span class="sxs-lookup"><span data-stu-id="337c5-217">Assemblies</span></span>

- <span data-ttu-id="337c5-218">✔️ **povoleno: sestavení přenositelného přenosného, pokud jsou stejné platformy stále podporovány**</span><span class="sxs-lookup"><span data-stu-id="337c5-218">✔️ **ALLOWED: Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="337c5-219">❌ **zakázané: Změna názvu sestavení**</span><span class="sxs-lookup"><span data-stu-id="337c5-219">❌ **DISALLOWED: Changing the name of an assembly**</span></span>
- <span data-ttu-id="337c5-220">❌ **zakázané: Změna veřejného klíče sestavení**</span><span class="sxs-lookup"><span data-stu-id="337c5-220">❌ **DISALLOWED: Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="337c5-221">Vlastnosti, pole, parametry a návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="337c5-221">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="337c5-222">✔️ **povoleno: Změna hodnoty vlastnosti, pole, návratové hodnoty nebo parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na více odvozený typ**</span><span class="sxs-lookup"><span data-stu-id="337c5-222">✔️ **ALLOWED: Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="337c5-223">Například metoda, která vrací typ <xref:System.Object> může vracet instanci <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="337c5-223">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="337c5-224">(Signatura metody se ale nemůže změnit.)</span><span class="sxs-lookup"><span data-stu-id="337c5-224">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="337c5-225">✔️ **povoleno: zvýšení rozsahu přípustných hodnot pro vlastnost nebo parametr, pokud člen není [virtuální](../../csharp/language-reference/keywords/virtual.md)**  .</span><span class="sxs-lookup"><span data-stu-id="337c5-225">✔️ **ALLOWED: Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="337c5-226">I když rozsah hodnot, které lze předat metodě nebo které mohou být vráceny členem, lze rozšířit, parametr nebo typ člena nemůže.</span><span class="sxs-lookup"><span data-stu-id="337c5-226">While the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="337c5-227">Například zatímco hodnoty předané metodě lze rozšířit z 0-124 na 0-255, typ parametru nemůže být změněn z <xref:System.Byte> na <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="337c5-227">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="337c5-228">❌ **zakázané: zvýšení rozsahu přípustných hodnot pro vlastnost nebo parametr, pokud je člen [virtuální](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="337c5-228">❌ **DISALLOWED: Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="337c5-229">Tato změna rozdělí existující přepsané členy, které nebudou správně fungovat pro rozšířený rozsah hodnot.</span><span class="sxs-lookup"><span data-stu-id="337c5-229">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="337c5-230">❌ **zakázané: zmenšení rozsahu přípustných hodnot pro vlastnost nebo parametr**</span><span class="sxs-lookup"><span data-stu-id="337c5-230">❌ **DISALLOWED: Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="337c5-231">❌ **zakázané: zvýšení rozsahu vrácených hodnot pro vlastnost, pole, návratovou hodnotu nebo [výstupní](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**</span><span class="sxs-lookup"><span data-stu-id="337c5-231">❌ **DISALLOWED: Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="337c5-232">❌ **zakázané: Změna vrácených hodnot pro vlastnost, pole, návratovou hodnotu metody nebo [výstupní](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**</span><span class="sxs-lookup"><span data-stu-id="337c5-232">❌ **DISALLOWED: Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="337c5-233">❌ **zakázané: Změna výchozí hodnoty vlastnosti, pole nebo parametru**</span><span class="sxs-lookup"><span data-stu-id="337c5-233">❌ **DISALLOWED: Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="337c5-234">❌ **zakázané: Změna přesnosti číselné návratové hodnoty**</span><span class="sxs-lookup"><span data-stu-id="337c5-234">❌ **DISALLOWED: Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="337c5-235">❓ **Vyžaduje rozhodnutí: Změna v analýze vstupu a vyvolání nových výjimek (i v případě, že se v dokumentaci nezadá chování při analýze).**</span><span class="sxs-lookup"><span data-stu-id="337c5-235">❓ **REQUIRES JUDGMENT: A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="337c5-236">Výjimky</span><span class="sxs-lookup"><span data-stu-id="337c5-236">Exceptions</span></span>

- <span data-ttu-id="337c5-237">✔️ **povoleno: vyvolání více odvozené výjimky, než je stávající výjimka**</span><span class="sxs-lookup"><span data-stu-id="337c5-237">✔️ **ALLOWED: Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="337c5-238">Vzhledem k tomu, že nová výjimka je podtřídou existující výjimky, pokračuje zpracování předchozí kódu zpracováním výjimky.</span><span class="sxs-lookup"><span data-stu-id="337c5-238">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="337c5-239">Například v .NET Framework 4 začaly metody vytváření a načítání jazykové verze vyvolávat <xref:System.Globalization.CultureNotFoundException> namísto <xref:System.ArgumentException>, pokud nebyla nalezena jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="337c5-239">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="337c5-240">Vzhledem k tomu, že <xref:System.Globalization.CultureNotFoundException> jsou odvozeny z <xref:System.ArgumentException>, jedná se o přijatelnou změnu.</span><span class="sxs-lookup"><span data-stu-id="337c5-240">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="337c5-241">✔️ **povoleno: byla aktivována konkrétnější výjimka než <xref:System.NotSupportedException>, <xref:System.NotImplementedException><xref:System.NullReferenceException>**</span><span class="sxs-lookup"><span data-stu-id="337c5-241">✔️ **ALLOWED: Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="337c5-242">✔️ **povoleno: probíhá vyvolání výjimky, která je považována za neodstranitelnou.**</span><span class="sxs-lookup"><span data-stu-id="337c5-242">✔️ **ALLOWED: Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="337c5-243">Neodstranitelné výjimky by neměly být zachyceny, ale místo toho by měly být zpracovány pomocí obslužné rutiny catch na vysoké úrovni.</span><span class="sxs-lookup"><span data-stu-id="337c5-243">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="337c5-244">Proto se neočekává, že uživatelé budou mít kód, který tyto explicitní výjimky zachytí.</span><span class="sxs-lookup"><span data-stu-id="337c5-244">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="337c5-245">Neobnovitelné výjimky jsou:</span><span class="sxs-lookup"><span data-stu-id="337c5-245">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="337c5-246">✔️ **povoleno: probíhá vyvolání nové výjimky v nové cestě kódu.**</span><span class="sxs-lookup"><span data-stu-id="337c5-246">✔️ **ALLOWED: Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="337c5-247">Výjimka se musí vztahovat jenom k nové cestě kódu, která se spustí s novými hodnotami parametrů nebo stavem a kterou nejde spustit pomocí stávajícího kódu, který cílí na předchozí verzi.</span><span class="sxs-lookup"><span data-stu-id="337c5-247">The exception must apply only to a new code-path that's executed with new parameter values or state and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="337c5-248">✔️ **povoleno: odebrání výjimky pro povolení robustnějšího chování nebo nových scénářů**</span><span class="sxs-lookup"><span data-stu-id="337c5-248">✔️ **ALLOWED: Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="337c5-249">Například `Divide` metoda, která dříve zpracovala pouze kladné hodnoty a vyvolala <xref:System.ArgumentOutOfRangeException> jinak může být změněna tak, aby podporovala záporné i kladné hodnoty bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="337c5-249">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="337c5-250">✔️ **povoleno: Změna textu chybové zprávy**</span><span class="sxs-lookup"><span data-stu-id="337c5-250">✔️ **ALLOWED: Changing the text of an error message**</span></span>

  <span data-ttu-id="337c5-251">Vývojáři by neměli spoléhat na text chybových zpráv, které se také mění v závislosti na jazykové verzi uživatele.</span><span class="sxs-lookup"><span data-stu-id="337c5-251">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="337c5-252">❌ **zakázané: vyvolává se výjimka v jakémkoli jiném případě, který není uvedený výše.**</span><span class="sxs-lookup"><span data-stu-id="337c5-252">❌ **DISALLOWED: Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="337c5-253">❌ **zakázané: odebrání výjimky v jakémkoli jiném případě, který není uvedený výše**</span><span class="sxs-lookup"><span data-stu-id="337c5-253">❌ **DISALLOWED: Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="337c5-254">Atributy</span><span class="sxs-lookup"><span data-stu-id="337c5-254">Attributes</span></span>

- <span data-ttu-id="337c5-255">✔️ **povoleno: Změna hodnoty atributu, který není *možné* pozorovat**</span><span class="sxs-lookup"><span data-stu-id="337c5-255">✔️ **ALLOWED: Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="337c5-256">❌ **zakázané: Změna hodnoty atributu, který *je* možné pozorovat**</span><span class="sxs-lookup"><span data-stu-id="337c5-256">❌ **DISALLOWED: Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="337c5-257">❓ **Vyžaduje rozhodnutí: odebrání atributu**</span><span class="sxs-lookup"><span data-stu-id="337c5-257">❓ **REQUIRES JUDGMENT: Removing an attribute**</span></span>

  <span data-ttu-id="337c5-258">Ve většině případů je odebrání atributu (například <xref:System.NonSerializedAttribute>) zásadní změnou.</span><span class="sxs-lookup"><span data-stu-id="337c5-258">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="337c5-259">Podpora platformy</span><span class="sxs-lookup"><span data-stu-id="337c5-259">Platform support</span></span>

- <span data-ttu-id="337c5-260">✔️ **povoleno: podpora operace na platformě, která nebyla dříve podporována**</span><span class="sxs-lookup"><span data-stu-id="337c5-260">✔️ **ALLOWED: Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="337c5-261">❌ **Nepovoleno: Nepodporováno nebo nyní nevyžaduje konkrétní aktualizaci Service Pack pro operaci, která byla dříve podporovaná na platformě.**</span><span class="sxs-lookup"><span data-stu-id="337c5-261">❌ **DISALLOWED: Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="337c5-262">Změny interní implementace</span><span class="sxs-lookup"><span data-stu-id="337c5-262">Internal implementation changes</span></span>

- <span data-ttu-id="337c5-263">❓ **Vyžaduje rozhodnutí: Změna oblasti povrchu interního typu**</span><span class="sxs-lookup"><span data-stu-id="337c5-263">❓ **REQUIRES JUDGMENT: Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="337c5-264">Tyto změny jsou obecně povoleny, i když přeruší soukromý odraz.</span><span class="sxs-lookup"><span data-stu-id="337c5-264">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="337c5-265">V některých případech, kde jsou oblíbené knihovny třetích stran nebo velký počet vývojářů závislé na interních rozhraních API, nemusí být tyto změny povolené.</span><span class="sxs-lookup"><span data-stu-id="337c5-265">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="337c5-266">❓ **Vyžaduje rozhodnutí: Změna interní implementace členu.**</span><span class="sxs-lookup"><span data-stu-id="337c5-266">❓ **REQUIRES JUDGMENT: Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="337c5-267">Tyto změny jsou obecně povoleny, i když přeruší soukromý odraz.</span><span class="sxs-lookup"><span data-stu-id="337c5-267">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="337c5-268">V některých případech, kde kód zákazníka často závisí na soukromé reflexi nebo kde změna zavádí nezamýšlené vedlejší účinky, nemusí být tyto změny povoleny.</span><span class="sxs-lookup"><span data-stu-id="337c5-268">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="337c5-269">✔️ **povoleno: zlepšení výkonu operace**</span><span class="sxs-lookup"><span data-stu-id="337c5-269">✔️ **ALLOWED: Improving the performance of an operation**</span></span>

   <span data-ttu-id="337c5-270">Možnost upravit výkon operace je zásadní, ale tyto změny mohou přerušit kód, který spoléhá na aktuální rychlost operace.</span><span class="sxs-lookup"><span data-stu-id="337c5-270">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="337c5-271">To platí zejména pro kód, který závisí na časování asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="337c5-271">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="337c5-272">Změna výkonu by neměla mít žádný vliv na jiné chování rozhraní API. v opačném případě bude změna zálomena.</span><span class="sxs-lookup"><span data-stu-id="337c5-272">The performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="337c5-273">✔️ **povoleno: nepřímo (a často nepříznivě) měnit výkon operace**</span><span class="sxs-lookup"><span data-stu-id="337c5-273">✔️ **ALLOWED: Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="337c5-274">Pokud se změna nedělí z nějakého jiného důvodu jako porušení, je to přijatelné.</span><span class="sxs-lookup"><span data-stu-id="337c5-274">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="337c5-275">Často je potřeba provést akce, které mohou zahrnovat dodatečné operace nebo které přidávají nové funkce.</span><span class="sxs-lookup"><span data-stu-id="337c5-275">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="337c5-276">To bude téměř vždy mít vliv na výkon, ale může být nezbytné, aby rozhraní API fungovalo podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="337c5-276">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="337c5-277">❌ **zakázané: Změna synchronního rozhraní API na asynchronní (a naopak)**</span><span class="sxs-lookup"><span data-stu-id="337c5-277">❌ **DISALLOWED: Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="337c5-278">Změny kódu</span><span class="sxs-lookup"><span data-stu-id="337c5-278">Code changes</span></span>

- <span data-ttu-id="337c5-279">✔️ **povoleno: přidání [parametrů](../../csharp/language-reference/keywords/params.md) do parametru**</span><span class="sxs-lookup"><span data-stu-id="337c5-279">✔️ **ALLOWED: Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="337c5-280">❌ **zakázané: Změna [struktury](../../csharp/language-reference/keywords/struct.md) na [třídu](../../csharp/language-reference/keywords/class.md) a naopak**</span><span class="sxs-lookup"><span data-stu-id="337c5-280">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/keywords/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="337c5-281">❌ **zakázané: přidání klíčového slova [checked](../../csharp/language-reference/keywords/virtual.md) do bloku kódu**</span><span class="sxs-lookup"><span data-stu-id="337c5-281">❌ **DISALLOWED: Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="337c5-282">Tato změna může způsobit, že kód, který dřív provedl k vyvolání <xref:System.OverflowException> a je nepřijatelný.</span><span class="sxs-lookup"><span data-stu-id="337c5-282">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="337c5-283">❌ **zakázané: odebírání [parametrů](../../csharp/language-reference/keywords/params.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="337c5-283">❌ **DISALLOWED: Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="337c5-284">❌ **zakázané: Změna pořadí, ve kterém se události aktivují**</span><span class="sxs-lookup"><span data-stu-id="337c5-284">❌ **DISALLOWED: Changing the order in which events are fired**</span></span>

  <span data-ttu-id="337c5-285">Vývojáři mohou rozumně očekávat, že události budou aktivovány ve stejném pořadí a kód pro vývojáře často závisí na pořadí, ve kterém jsou události vyvolány.</span><span class="sxs-lookup"><span data-stu-id="337c5-285">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="337c5-286">❌ **zakázané: odebrání vyvolání události na dané akci**</span><span class="sxs-lookup"><span data-stu-id="337c5-286">❌ **DISALLOWED: Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="337c5-287">❌ **zakázané: Změna počtu volání daných událostí**</span><span class="sxs-lookup"><span data-stu-id="337c5-287">❌ **DISALLOWED: Changing the number of times given events are called**</span></span>

- <span data-ttu-id="337c5-288">❌ **zakázané: přidání <xref:System.FlagsAttribute> do výčtového typu**</span><span class="sxs-lookup"><span data-stu-id="337c5-288">❌ **DISALLOWED: Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>

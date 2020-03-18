---
title: Typy přerušovatých změn
description: Zjistěte, jak se rozhraní .NET Core pokouší zachovat kompatibilitu pro vývojáře ve verzích rozhraní .NET a jaký druh změny je považován za narušující změnu.
ms.date: 06/10/2019
ms.openlocfilehash: bf0cc35d69e6bb501640455604a99a1f48962c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628589"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="aa322-103">Změny, které ovlivňují kompatibilitu</span><span class="sxs-lookup"><span data-stu-id="aa322-103">Changes that affect compatibility</span></span>

<span data-ttu-id="aa322-104">V průběhu své historie .NET se pokusil a udržovat vysokou úroveň kompatibility z verze na verzi a napříč variantami .NET.</span><span class="sxs-lookup"><span data-stu-id="aa322-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="aa322-105">To platí i nadále pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aa322-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="aa322-106">Přestože .NET Core lze považovat za novou technologii, která je nezávislá na rozhraní .NET Framework, dva hlavní faktory omezují schopnost .NET Core odchýlit se od rozhraní .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="aa322-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="aa322-107">Velký počet vývojářů původně vyvinutý nebo pokračovat ve vývoji aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa322-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="aa322-108">Očekávají konzistentní chování napříč implementacemi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="aa322-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="aa322-109">Projekty knihovny .NET Standard umožňují vývojářům vytvářet knihovny, které cílí na běžná rozhraní API sdílená rozhraními .NET Core a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa322-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="aa322-110">Vývojáři očekávají, že knihovna použitá v aplikaci .NET Core by se měla chovat stejně jako stejná knihovna používaná v aplikaci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa322-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="aa322-111">Spolu s kompatibilitou napříč implementacemi rozhraní .NET vývojáři očekávají vysokou úroveň kompatibility napříč verzemi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aa322-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="aa322-112">Zejména kód napsaný pro starší verzi rozhraní .NET Core by měl běžet bez problémů v novější verzi rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aa322-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="aa322-113">Ve skutečnosti mnoho vývojářů očekává, že nová rozhraní API nalezená v nově vydaných verzích rozhraní .NET Core by měla být také kompatibilní s předběžnými verzemi, ve kterých byla tato rozhraní API zavedena.</span><span class="sxs-lookup"><span data-stu-id="aa322-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="aa322-114">Tento článek popisuje kategorie změny kompatibility (nebo narušující změny) a způsob, jakým tým .NET vyhodnocuje změny v každé z těchto kategorií.</span><span class="sxs-lookup"><span data-stu-id="aa322-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="aa322-115">Pochopení toho, jak tým .NET přistupuje k možným narušujícím změnám, je užitečné zejména pro vývojáře, kteří otevírají žádosti o přijetí změn v úložišti GitHub [dotnet/runtime,](https://github.com/dotnet/runtime) které mění chování existujících rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="aa322-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests in the [dotnet/runtime](https://github.com/dotnet/runtime) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="aa322-116">Definice kategorií kompatibility, jako je například binární kompatibilita a zpětná kompatibilita, naleznete [v tématu Breaking change categories](categories.md).</span><span class="sxs-lookup"><span data-stu-id="aa322-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="aa322-117">Následující části popisují kategorie změn provedených rozhraní API .NET Core a jejich dopad na kompatibilitu aplikací.</span><span class="sxs-lookup"><span data-stu-id="aa322-117">The following sections describe the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="aa322-118">Změny jsou buď povoleny ❌✔️, zakázáno , nebo vyžadují úsudek a hodnocení toho, jak předvídatelné, zřejmé a konzistentní předchozí chování bylo ❓.</span><span class="sxs-lookup"><span data-stu-id="aa322-118">Changes are either allowed ✔️, disallowed ❌, or require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was ❓.</span></span>

> [!NOTE]
> <span data-ttu-id="aa322-119">Kromě toho, že slouží jako vodítko pro vyhodnocování změn v knihovnách .NET Core, mohou vývojáři knihovny také použít tato kritéria k vyhodnocení změn v jejich knihovnách, které cílí na více implementací a verzí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="aa322-119">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="aa322-120">Změny veřejné zakázky</span><span class="sxs-lookup"><span data-stu-id="aa322-120">Modifications to the public contract</span></span>

<span data-ttu-id="aa322-121">Změny v této kategorii upravují veřejnou plochu typu.</span><span class="sxs-lookup"><span data-stu-id="aa322-121">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="aa322-122">Většina změn v této kategorii jsou zakázány, protože porušují *zpětnou kompatibilitu* (schopnost aplikace, která byla vyvinuta s předchozí verzí rozhraní API spustit bez rekompilace v novější verzi).</span><span class="sxs-lookup"><span data-stu-id="aa322-122">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="aa322-123">Typy</span><span class="sxs-lookup"><span data-stu-id="aa322-123">Types</span></span>

- <span data-ttu-id="aa322-124">✔️ **povoleno: Odebrání implementace rozhraní z typu, když je rozhraní již implementováno základním typem**</span><span class="sxs-lookup"><span data-stu-id="aa322-124">✔️ **ALLOWED: Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="aa322-125">❓ **vyžaduje úsudek: Přidání nové implementace rozhraní typu**</span><span class="sxs-lookup"><span data-stu-id="aa322-125">❓ **REQUIRES JUDGMENT: Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="aa322-126">Jedná se o přijatelnou změnu, protože nemá nepříznivý vliv na stávající klienty.</span><span class="sxs-lookup"><span data-stu-id="aa322-126">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="aa322-127">Všechny změny typu musí fungovat v rámci hranic přijatelné změny definované zde pro nové implementace zůstat přijatelné.</span><span class="sxs-lookup"><span data-stu-id="aa322-127">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="aa322-128">Extrémní opatrnost je nutná při přidávání rozhraní, které přímo ovlivňují schopnost návrháře nebo serializátoru generovat kód nebo data, která nelze spotřebovat na nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="aa322-128">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="aa322-129">Příkladem je <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa322-129">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="aa322-130">❓ **vyžaduje úsudek: Zavedení nové základní třídy**</span><span class="sxs-lookup"><span data-stu-id="aa322-130">❓ **REQUIRES JUDGMENT: Introducing a new base class**</span></span>

  <span data-ttu-id="aa322-131">Typ může být zaveden do hierarchie mezi dvěma existujícími typy, pokud nezavádí žádné nové [abstraktní](../../csharp/language-reference/keywords/abstract.md) členy nebo nemění sémantiku nebo chování existujících typů.</span><span class="sxs-lookup"><span data-stu-id="aa322-131">A type can be introduced into a hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="aa322-132">Například v rozhraní .NET Framework <xref:System.Data.Common.DbConnection> 2.0 se třída <xref:System.Data.SqlClient.SqlConnection>stala novou základní třídou pro , která byla dříve odvozena přímo z . <xref:System.ComponentModel.Component></span><span class="sxs-lookup"><span data-stu-id="aa322-132">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="aa322-133">✔️ **povoleno: Přesunutí typu z jedné sestavy do druhé**</span><span class="sxs-lookup"><span data-stu-id="aa322-133">✔️ **ALLOWED: Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="aa322-134">*Staré* sestavení musí být <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> označeno, které odkazuje na nové sestavení.</span><span class="sxs-lookup"><span data-stu-id="aa322-134">The *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="aa322-135">✔️ **povoleno: [struct](../../csharp/language-reference/builtin-types/struct.md) Změna typu struktury `readonly struct` na typ**</span><span class="sxs-lookup"><span data-stu-id="aa322-135">✔️ **ALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="aa322-136">Změna `readonly struct` typu na `struct` typ není povolena.</span><span class="sxs-lookup"><span data-stu-id="aa322-136">Changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="aa322-137">✔️ **povoleno: Přidání [zapečetěného](../../csharp/language-reference/keywords/sealed.md) nebo [abstraktního](../../csharp/language-reference/keywords/abstract.md) klíčového slova k typu, pokud neexistují žádné *přístupné* (veřejné nebo chráněné) konstruktory**</span><span class="sxs-lookup"><span data-stu-id="aa322-137">✔️ **ALLOWED: Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="aa322-138">✔️ **povoleno: Rozšíření viditelnosti typu**</span><span class="sxs-lookup"><span data-stu-id="aa322-138">✔️ **ALLOWED: Expanding the visibility of a type**</span></span>

- <span data-ttu-id="aa322-139">❌**Zakázáno: Změna oboru názvů nebo názvu typu**</span><span class="sxs-lookup"><span data-stu-id="aa322-139">❌ **DISALLOWED: Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="aa322-140">❌**Zakázáno: Přejmenování nebo odebrání veřejného typu**</span><span class="sxs-lookup"><span data-stu-id="aa322-140">❌ **DISALLOWED: Renaming or removing a public type**</span></span>

   <span data-ttu-id="aa322-141">Tím se rozdělí veškerý kód, který používá přejmenovaný nebo odebraný typ.</span><span class="sxs-lookup"><span data-stu-id="aa322-141">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="aa322-142">❌**Zakázáno: Změna základního typu výčtu**</span><span class="sxs-lookup"><span data-stu-id="aa322-142">❌ **DISALLOWED: Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="aa322-143">Toto je změna kompilace a chování lámání, stejně jako binární zalomení změny, které mohou atribut argumenty neopravitelné.</span><span class="sxs-lookup"><span data-stu-id="aa322-143">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="aa322-144">❌**Zakázáno: Zapečetění typu, který byl dříve nezapečetěný**</span><span class="sxs-lookup"><span data-stu-id="aa322-144">❌ **DISALLOWED: Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="aa322-145">❌**Zakázáno: Přidání rozhraní do sady základních typů rozhraní**</span><span class="sxs-lookup"><span data-stu-id="aa322-145">❌ **DISALLOWED: Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="aa322-146">Pokud rozhraní implementuje rozhraní, které dříve neimplementoval, jsou poškozeny všechny typy, které implementovaly původní verzi rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa322-146">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="aa322-147">❓ **vyžaduje úsudek: Odebrání třídy ze sady základních tříd nebo rozhraní ze sady implementovaných rozhraní**</span><span class="sxs-lookup"><span data-stu-id="aa322-147">❓ **REQUIRES JUDGMENT: Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="aa322-148">Existuje jedna výjimka z pravidla pro odebrání rozhraní: můžete přidat implementaci rozhraní, které je odvozeno z odebraného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa322-148">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="aa322-149">Můžete například odebrat, <xref:System.IDisposable> pokud typ nebo <xref:System.ComponentModel.IComponent>rozhraní nyní <xref:System.IDisposable>implementuje , který implementuje .</span><span class="sxs-lookup"><span data-stu-id="aa322-149">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="aa322-150">❌**Zakázáno: Změna `readonly struct` typu [na](../../csharp/language-reference/builtin-types/struct.md) typ struktury**</span><span class="sxs-lookup"><span data-stu-id="aa322-150">❌ **DISALLOWED: Changing a `readonly struct` type to a [struct](../../csharp/language-reference/builtin-types/struct.md) type**</span></span>

  <span data-ttu-id="aa322-151">Změna `struct` typu typu `readonly struct` je však povolena.</span><span class="sxs-lookup"><span data-stu-id="aa322-151">The change of a `struct` type to a `readonly struct` type is allowed, however.</span></span>

- <span data-ttu-id="aa322-152">❌**Zakázáno: Změna typu [struktury](../../csharp/language-reference/builtin-types/struct.md) na `ref struct` typ a naopak.**</span><span class="sxs-lookup"><span data-stu-id="aa322-152">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="aa322-153">❌**Zakázáno: Snížení viditelnosti typu**</span><span class="sxs-lookup"><span data-stu-id="aa322-153">❌ **DISALLOWED: Reducing the visibility of a type**</span></span>

   <span data-ttu-id="aa322-154">Zvýšení viditelnosti typu je však povoleno.</span><span class="sxs-lookup"><span data-stu-id="aa322-154">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="aa322-155">Členové</span><span class="sxs-lookup"><span data-stu-id="aa322-155">Members</span></span>

- <span data-ttu-id="aa322-156">✔️ \*\*povoleno: Rozšíření viditelnosti člena, který není [virtuální](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="aa322-156">✔️ **ALLOWED: Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="aa322-157">✔️ \*\*povoleno: Přidání abstraktního člena do veřejného typu, který nemá žádné *přístupné* (veřejné nebo chráněné) konstruktory, nebo je [zapečetěný typ.](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="aa322-157">✔️ **ALLOWED: Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="aa322-158">Přidání abstraktního člena do typu, který má přístupné (veřejné nebo `sealed` chráněné) konstruktory a není povoleno.</span><span class="sxs-lookup"><span data-stu-id="aa322-158">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="aa322-159">✔️ \*\*povoleno: Omezení viditelnosti [chráněného](../../csharp/language-reference/keywords/protected.md) člena, pokud typ nemá přístupné (veřejné nebo chráněné) konstruktory nebo je typ [zapečetěný](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="aa322-159">✔️ **ALLOWED: Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="aa322-160">✔️ **povoleno: Přesunutí člena do třídy vyšší v hierarchii, než je typ, ze kterého byl odebrán**</span><span class="sxs-lookup"><span data-stu-id="aa322-160">✔️ **ALLOWED: Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="aa322-161">✔️ **povoleno: Přidání nebo odebrání přepsání**</span><span class="sxs-lookup"><span data-stu-id="aa322-161">✔️ **ALLOWED: Adding or removing an override**</span></span>

  <span data-ttu-id="aa322-162">Zavedení přepsání může způsobit, že předchozí spotřebitelé přeskočí přepsání při volání [base](../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="aa322-162">Introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="aa322-163">✔️ **povoleno: Přidání konstruktoru do třídy, spolu s konstruktorem bez parametrů, pokud třída dříve neměla žádné konstruktory**</span><span class="sxs-lookup"><span data-stu-id="aa322-163">✔️ **ALLOWED: Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="aa322-164">Přidání konstruktoru do třídy, která dříve neměla žádné konstruktory *bez* přidání konstruktoru bez parametrů, však není povoleno.</span><span class="sxs-lookup"><span data-stu-id="aa322-164">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="aa322-165">✔️ \*\*povoleno: Změna člena z [abstraktního](../../csharp/language-reference/keywords/abstract.md) na [virtuální](../../csharp/language-reference/keywords/virtual.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="aa322-165">✔️ **ALLOWED: Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="aa322-166">✔️ **povoleno: Přechod `ref readonly` z `ref` a na vrácenou hodnotu (s výjimkou virtuálních metod nebo rozhraní)**</span><span class="sxs-lookup"><span data-stu-id="aa322-166">✔️ **ALLOWED: Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="aa322-167">✔️ **povoleno: Odebrání [pouze pro čtení](../../csharp/language-reference/keywords/readonly.md) z pole, pokud statický typ pole není proměnlivý typ hodnoty**</span><span class="sxs-lookup"><span data-stu-id="aa322-167">✔️ **ALLOWED: Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="aa322-168">✔️ **povoleno: Volání nové události, která nebyla dříve definována**</span><span class="sxs-lookup"><span data-stu-id="aa322-168">✔️ **ALLOWED: Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="aa322-169">❓ **vyžaduje úsudek: Přidání pole nové instance k typu**</span><span class="sxs-lookup"><span data-stu-id="aa322-169">❓ **REQUIRES JUDGMENT: Adding a new instance field to a type**</span></span>

   <span data-ttu-id="aa322-170">Tato změna má vliv na serializaci.</span><span class="sxs-lookup"><span data-stu-id="aa322-170">This change impacts serialization.</span></span>

- <span data-ttu-id="aa322-171">❌**Zakázáno: Přejmenování nebo odebrání veřejného člena nebo parametru**</span><span class="sxs-lookup"><span data-stu-id="aa322-171">❌ **DISALLOWED: Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="aa322-172">Tím se rozdělí veškerý kód, který používá přejmenovaný nebo odebraný člen nebo parametr.</span><span class="sxs-lookup"><span data-stu-id="aa322-172">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="aa322-173">To zahrnuje odebrání nebo přejmenování getter nebo setter z vlastnosti, jakož i přejmenování nebo odebrání členů výčtu.</span><span class="sxs-lookup"><span data-stu-id="aa322-173">This includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="aa322-174">❌**Zakázáno: Přidání člena do rozhraní**</span><span class="sxs-lookup"><span data-stu-id="aa322-174">❌ **DISALLOWED: Adding a member to an interface**</span></span>

- <span data-ttu-id="aa322-175">❌**Zakázáno: Změna hodnoty veřejné konstanty nebo člena výčtu**</span><span class="sxs-lookup"><span data-stu-id="aa322-175">❌ **DISALLOWED: Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="aa322-176">❌**Zakázáno: Změna typu vlastnosti, pole, parametru nebo vrácené hodnoty**</span><span class="sxs-lookup"><span data-stu-id="aa322-176">❌ **DISALLOWED: Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="aa322-177">❌**Zakázáno: Přidání, odebrání nebo změna pořadí parametrů**</span><span class="sxs-lookup"><span data-stu-id="aa322-177">❌ **DISALLOWED: Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="aa322-178">❌**Zakázáno: Přidání nebo odebrání klíčového slova [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) nebo [ref](../../csharp/language-reference/keywords/ref.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="aa322-178">❌ **DISALLOWED: Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="aa322-179">❌**Zakázáno: Přejmenování parametru (včetně změny jeho případu)**</span><span class="sxs-lookup"><span data-stu-id="aa322-179">❌ **DISALLOWED: Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="aa322-180">To je považováno za porušení ze dvou důvodů:</span><span class="sxs-lookup"><span data-stu-id="aa322-180">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="aa322-181">Přeruší scénáře s pozdní vazbou, jako je například funkce pozdní vazby v jazyce Visual Basic a [dynamické](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="aa322-181">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="aa322-182">Přeruší [kompatibilitu zdroje,](categories.md#source-compatibility) když vývojáři používají [pojmenované argumenty](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span><span class="sxs-lookup"><span data-stu-id="aa322-182">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="aa322-183">❌**Zakázáno: Změna z `ref` vrácené `ref readonly` hodnoty na vrácenou hodnotu**</span><span class="sxs-lookup"><span data-stu-id="aa322-183">❌ **DISALLOWED: Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="aa322-184">❌️**Zakázáno: Přechod z `ref readonly` a `ref` na vrácenou hodnotu na virtuální metodu nebo rozhraní**</span><span class="sxs-lookup"><span data-stu-id="aa322-184">❌️ **DISALLOWED: Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="aa322-185">❌**Zakázáno: Přidání nebo odebrání [abstraktu](../../csharp/language-reference/keywords/abstract.md) z člena**</span><span class="sxs-lookup"><span data-stu-id="aa322-185">❌ **DISALLOWED: Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="aa322-186">❌**Zakázáno: Odebrání [virtuálního](../../csharp/language-reference/keywords/virtual.md) klíčového slova z člena**</span><span class="sxs-lookup"><span data-stu-id="aa322-186">❌ **DISALLOWED: Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="aa322-187">I když to často není narušující změna, protože kompilátor Jazyka C# má tendenci vyzařovat pokyny`callvirt` pro volání zprostředkujícího jazyka [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) (IL) pro volání nevirtuálních metod (provádí kontrolu null, zatímco normální volání není), toto chování není neměnné z několika důvodů:</span><span class="sxs-lookup"><span data-stu-id="aa322-187">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="aa322-188">C# není jediný jazyk, který .NET cíle.</span><span class="sxs-lookup"><span data-stu-id="aa322-188">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="aa322-189">Kompilátor Jazyka C# `callvirt` se stále více pokouší optimalizovat na normální volání vždy, když je metoda target nevirtuální a pravděpodobně není null (například metoda přístupná prostřednictvím [operátoru šíření null ).](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="aa322-189">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="aa322-190">Vytvoření virtuální metody znamená, že kód příjemce by často skončí volání mj.</span><span class="sxs-lookup"><span data-stu-id="aa322-190">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="aa322-191">❌**Zakázáno: Přidání [virtuálního](../../csharp/language-reference/keywords/virtual.md) klíčového slova do člena**</span><span class="sxs-lookup"><span data-stu-id="aa322-191">❌ **DISALLOWED: Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="aa322-192">❌**Zakázáno: Vytvoření abstraktního virtuálního člena**</span><span class="sxs-lookup"><span data-stu-id="aa322-192">❌ **DISALLOWED: Making a virtual member abstract**</span></span>

  <span data-ttu-id="aa322-193">[Virtuální člen](../../csharp/language-reference/keywords/virtual.md) poskytuje implementaci metody, která *může být* přepsána odvozenou třídou.</span><span class="sxs-lookup"><span data-stu-id="aa322-193">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="aa322-194">[Abstraktní člen](../../csharp/language-reference/keywords/abstract.md) poskytuje žádnou implementaci a *musí být* přepsán.</span><span class="sxs-lookup"><span data-stu-id="aa322-194">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="aa322-195">❌\*\*Zakázáno: Přidání abstraktního člena do veřejného typu, který má přístupné (veřejné nebo chráněné) konstruktory a který není [zapečetěný](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="aa322-195">❌ **DISALLOWED: Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="aa322-196">❌**Zakázáno: Přidání nebo odebrání [statického](../../csharp/language-reference/keywords/static.md) klíčového slova z člena**</span><span class="sxs-lookup"><span data-stu-id="aa322-196">❌ **DISALLOWED: Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="aa322-197">❌**Zakázáno: Přidání přetížení, které vylučuje existující přetížení a definuje jiné chování**</span><span class="sxs-lookup"><span data-stu-id="aa322-197">❌ **DISALLOWED: Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="aa322-198">Tím se přeruší existující klienti, kteří byli vázáni na předchozí přetížení.</span><span class="sxs-lookup"><span data-stu-id="aa322-198">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="aa322-199">Například pokud třída má jednu verzi metody, <xref:System.UInt32>která přijímá , existující příjemce bude úspěšně <xref:System.Int32> vázat na toto přetížení při předávání hodnoty.</span><span class="sxs-lookup"><span data-stu-id="aa322-199">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="aa322-200">Však pokud přidáte přetížení, které <xref:System.Int32>přijímá , při rekompilaci nebo pomocí pozdní vazby, kompilátor nyní váže na nové přetížení.</span><span class="sxs-lookup"><span data-stu-id="aa322-200">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="aa322-201">Pokud dojde k odlišnému chování, jedná se o narušující změnu.</span><span class="sxs-lookup"><span data-stu-id="aa322-201">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="aa322-202">❌**Zakázáno: Přidání konstruktoru do třídy, která dříve neměla žádný konstruktor bez přidání konstruktoru bez parametrů**</span><span class="sxs-lookup"><span data-stu-id="aa322-202">❌ **DISALLOWED: Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="aa322-203">❌️**Zakázáno: Přidání [pouze pro čtení](../../csharp/language-reference/keywords/readonly.md) do pole**</span><span class="sxs-lookup"><span data-stu-id="aa322-203">❌️ **DISALLOWED: Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="aa322-204">❌**Zakázáno: Snížení viditelnosti člena**</span><span class="sxs-lookup"><span data-stu-id="aa322-204">❌ **DISALLOWED: Reducing the visibility of a member**</span></span>

   <span data-ttu-id="aa322-205">To zahrnuje snížení viditelnosti [chráněného](../../csharp/language-reference/keywords/protected.md) prvku, pokud`public` `protected`jsou *přístupné* ( nebo ) konstruktory a typ *není* [zapečetěn .](../../csharp/language-reference/keywords/sealed.md)</span><span class="sxs-lookup"><span data-stu-id="aa322-205">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (`public` or `protected`) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="aa322-206">Pokud tomu tak není, je povoleno snížení viditelnosti chráněného člena.</span><span class="sxs-lookup"><span data-stu-id="aa322-206">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="aa322-207">Zvýšení viditelnosti člena je povoleno.</span><span class="sxs-lookup"><span data-stu-id="aa322-207">Increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="aa322-208">❌**Zakázáno: Změna typu člena**</span><span class="sxs-lookup"><span data-stu-id="aa322-208">❌ **DISALLOWED: Changing the type of a member**</span></span>

   <span data-ttu-id="aa322-209">Vrácenou hodnotu metody nebo typu vlastnosti nebo pole nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="aa322-209">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="aa322-210">Například podpis metody, která vrací <xref:System.Object> nelze změnit vrátit <xref:System.String>, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="aa322-210">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="aa322-211">❌**Zakázáno: Přidání pole do struktury, která dříve neměla žádný stav**</span><span class="sxs-lookup"><span data-stu-id="aa322-211">❌ **DISALLOWED: Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="aa322-212">Pravidla jednoznačného přiřazení umožňují použití neinicializovaných proměnných, pokud je typ proměnné strukturou bez stavů.</span><span class="sxs-lookup"><span data-stu-id="aa322-212">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="aa322-213">Pokud je struktura provedena stavové, kód může skončit s neinicializovaných dat.</span><span class="sxs-lookup"><span data-stu-id="aa322-213">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="aa322-214">Toto je potenciálně zdroj rozdělení a binární rozdělení změny.</span><span class="sxs-lookup"><span data-stu-id="aa322-214">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="aa322-215">❌**Zakázáno: Spuštění existující události, když nebyla nikdy předtím aktivována**</span><span class="sxs-lookup"><span data-stu-id="aa322-215">❌ **DISALLOWED: Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="aa322-216">Změny chování</span><span class="sxs-lookup"><span data-stu-id="aa322-216">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="aa322-217">Sestavení</span><span class="sxs-lookup"><span data-stu-id="aa322-217">Assemblies</span></span>

- <span data-ttu-id="aa322-218">✔️ **povoleno: Vytvoření přenosné sestavy, pokud jsou stále podporovány stejné platformy**</span><span class="sxs-lookup"><span data-stu-id="aa322-218">✔️ **ALLOWED: Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="aa322-219">❌**Zakázáno: Změna názvu sestavení**</span><span class="sxs-lookup"><span data-stu-id="aa322-219">❌ **DISALLOWED: Changing the name of an assembly**</span></span>
- <span data-ttu-id="aa322-220">❌**Zakázáno: Změna veřejného klíče sestavení**</span><span class="sxs-lookup"><span data-stu-id="aa322-220">❌ **DISALLOWED: Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="aa322-221">Vlastnosti, pole, parametry a vrácené hodnoty</span><span class="sxs-lookup"><span data-stu-id="aa322-221">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="aa322-222">✔️ **povoleno: Změna hodnoty vlastnosti, pole, vrácené hodnoty nebo parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na odvozenější typ**</span><span class="sxs-lookup"><span data-stu-id="aa322-222">✔️ **ALLOWED: Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="aa322-223">Například metoda, která vrací <xref:System.Object> typ může <xref:System.String> vrátit instanci.</span><span class="sxs-lookup"><span data-stu-id="aa322-223">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="aa322-224">(Podpis metody se však nemůže změnit.)</span><span class="sxs-lookup"><span data-stu-id="aa322-224">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="aa322-225">✔️ \*\*povoleno: Zvýšení rozsahu přijatých hodnot pro vlastnost nebo parametr, pokud člen není [virtuální](../../csharp/language-reference/keywords/virtual.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="aa322-225">✔️ **ALLOWED: Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="aa322-226">Zatímco rozsah hodnot, které mohou být předány metodě nebo jsou vráceny členem lze rozšířit, parametr nebo typ člena nelze.</span><span class="sxs-lookup"><span data-stu-id="aa322-226">While the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="aa322-227">Například zatímco hodnoty předané metodě lze rozšířit z 0-124 na 0-255, typ parametru nelze změnit z na <xref:System.Byte> <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="aa322-227">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="aa322-228">❌\*\*Zakázáno: Zvýšení rozsahu přijatých hodnot pro vlastnost nebo parametr, pokud je člen [virtuální](../../csharp/language-reference/keywords/virtual.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="aa322-228">❌ **DISALLOWED: Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="aa322-229">Tato změna přeruší existující přepsané členy, které nebudou fungovat správně pro rozšířený rozsah hodnot.</span><span class="sxs-lookup"><span data-stu-id="aa322-229">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="aa322-230">❌**Zakázáno: Snížení rozsahu přijatých hodnot pro vlastnost nebo parametr**</span><span class="sxs-lookup"><span data-stu-id="aa322-230">❌ **DISALLOWED: Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="aa322-231">❌**Zakázáno: Zvýšení rozsahu vrácených hodnot pro parametr vlastnost, [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) pole, vrácenou hodnotu nebo out parametr**</span><span class="sxs-lookup"><span data-stu-id="aa322-231">❌ **DISALLOWED: Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="aa322-232">❌\*\*Zakázáno: Změna vrácených hodnot pro vlastnost, pole, vrácenou hodnotu metody nebo parametr [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="aa322-232">❌ **DISALLOWED: Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="aa322-233">❌**Zakázáno: Změna výchozí hodnoty vlastnosti, pole nebo parametru**</span><span class="sxs-lookup"><span data-stu-id="aa322-233">❌ **DISALLOWED: Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="aa322-234">❌**Zakázáno: Změna přesnosti číselné vrácené hodnoty**</span><span class="sxs-lookup"><span data-stu-id="aa322-234">❌ **DISALLOWED: Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="aa322-235">❓ **vyžaduje úsudek: Změna analýzy vstupu a vyvolání nových výjimek (i když chování analýzy není specifikováno v dokumentaci**</span><span class="sxs-lookup"><span data-stu-id="aa322-235">❓ **REQUIRES JUDGMENT: A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="aa322-236">Výjimky</span><span class="sxs-lookup"><span data-stu-id="aa322-236">Exceptions</span></span>

- <span data-ttu-id="aa322-237">✔️ **povoleno: Vyvolání více odvozené výjimky než existující výjimky**</span><span class="sxs-lookup"><span data-stu-id="aa322-237">✔️ **ALLOWED: Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="aa322-238">Vzhledem k tomu, že nová výjimka je podtřídou existující výjimky, předchozí kód zpracování výjimek pokračuje ve zpracování výjimky.</span><span class="sxs-lookup"><span data-stu-id="aa322-238">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="aa322-239">Například v rozhraní .NET Framework 4 metody vytváření a <xref:System.Globalization.CultureNotFoundException> načítání <xref:System.ArgumentException> jazykové verze začaly vyvolávat místo, pokud nelze nalézt jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="aa322-239">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="aa322-240">Protože <xref:System.Globalization.CultureNotFoundException> pochází <xref:System.ArgumentException>z , jedná se o přijatelnou změnu.</span><span class="sxs-lookup"><span data-stu-id="aa322-240">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="aa322-241">✔️ **povoleno: Vyvolání konkrétnější <xref:System.NotSupportedException>výjimky <xref:System.NullReferenceException> než , <xref:System.NotImplementedException>**</span><span class="sxs-lookup"><span data-stu-id="aa322-241">✔️ **ALLOWED: Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="aa322-242">✔️ **povoleno: Vyvolání výjimky, která je považována za neopravitelnou**</span><span class="sxs-lookup"><span data-stu-id="aa322-242">✔️ **ALLOWED: Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="aa322-243">Neopravitelné výjimky by neměly být zachyceny, ale místo toho by měly být zpracovány obslužnou rutinou catch-all na vysoké úrovni.</span><span class="sxs-lookup"><span data-stu-id="aa322-243">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="aa322-244">Proto se neočekává, že uživatelé mají kód, který zachycuje tyto explicitní výjimky.</span><span class="sxs-lookup"><span data-stu-id="aa322-244">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="aa322-245">Neopravitelné výjimky jsou:</span><span class="sxs-lookup"><span data-stu-id="aa322-245">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="aa322-246">✔️ **povoleno: Vyvolání nové výjimky v nové cestě kódu**</span><span class="sxs-lookup"><span data-stu-id="aa322-246">✔️ **ALLOWED: Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="aa322-247">Výjimka se musí vztahovat pouze na novou cestu kódu, která je spuštěna s novými hodnotami parametrů nebo stavem a kterou nelze provést existujícím kódem, který cílí na předchozí verzi.</span><span class="sxs-lookup"><span data-stu-id="aa322-247">The exception must apply only to a new code-path that's executed with new parameter values or state and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="aa322-248">✔️ **povoleno: Odebrání výjimky pro povolení robustnějšího chování nebo nových scénářů**</span><span class="sxs-lookup"><span data-stu-id="aa322-248">✔️ **ALLOWED: Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="aa322-249">Například `Divide` metoda, která dříve zpracovávala pouze <xref:System.ArgumentOutOfRangeException> kladné hodnoty a jinak vyvolala jinak, může být změněna tak, aby podporovala záporné i kladné hodnoty bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="aa322-249">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="aa322-250">✔️ **povoleno: Změna textu chybové zprávy**</span><span class="sxs-lookup"><span data-stu-id="aa322-250">✔️ **ALLOWED: Changing the text of an error message**</span></span>

  <span data-ttu-id="aa322-251">Vývojáři by neměli spoléhat na text chybových zpráv, které se také mění na základě jazykové verze uživatele.</span><span class="sxs-lookup"><span data-stu-id="aa322-251">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="aa322-252">❌**Zakázáno: Vyvolání výjimky v jakémkoli jiném případě, který není uveden výše**</span><span class="sxs-lookup"><span data-stu-id="aa322-252">❌ **DISALLOWED: Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="aa322-253">❌**Zakázáno: Odebrání výjimky v jakémkoli jiném případě, který není uveden výše.**</span><span class="sxs-lookup"><span data-stu-id="aa322-253">❌ **DISALLOWED: Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="aa322-254">Atributy</span><span class="sxs-lookup"><span data-stu-id="aa322-254">Attributes</span></span>

- <span data-ttu-id="aa322-255">✔️ **povoleno: Změna hodnoty atributu, který *není* pozorovatelný**</span><span class="sxs-lookup"><span data-stu-id="aa322-255">✔️ **ALLOWED: Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="aa322-256">❌**Zakázáno: Změna hodnoty atributu, který *je* pozorovatelný**</span><span class="sxs-lookup"><span data-stu-id="aa322-256">❌ **DISALLOWED: Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="aa322-257">❓ **vyžaduje úsudek: Odebrání atributu**</span><span class="sxs-lookup"><span data-stu-id="aa322-257">❓ **REQUIRES JUDGMENT: Removing an attribute**</span></span>

  <span data-ttu-id="aa322-258">Ve většině případů je odebrání <xref:System.NonSerializedAttribute>atributu (například) narušující změnou.</span><span class="sxs-lookup"><span data-stu-id="aa322-258">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="aa322-259">Podpora platformy</span><span class="sxs-lookup"><span data-stu-id="aa322-259">Platform support</span></span>

- <span data-ttu-id="aa322-260">✔️ **povoleno: Podpora operace na platformě, která dříve nebyla podporována**</span><span class="sxs-lookup"><span data-stu-id="aa322-260">✔️ **ALLOWED: Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="aa322-261">❌**Zakázáno: Nepodporuje nebo nyní vyžaduje konkrétní aktualizaci Service Pack pro operaci, která byla dříve podporována na platformě**</span><span class="sxs-lookup"><span data-stu-id="aa322-261">❌ **DISALLOWED: Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="aa322-262">Změny interní implementace</span><span class="sxs-lookup"><span data-stu-id="aa322-262">Internal implementation changes</span></span>

- <span data-ttu-id="aa322-263">❓ **vyžaduje úsudek: Změna plochy vnitřního typu**</span><span class="sxs-lookup"><span data-stu-id="aa322-263">❓ **REQUIRES JUDGMENT: Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="aa322-264">Takové změny jsou obecně povoleny, i když porušují soukromé reflexe.</span><span class="sxs-lookup"><span data-stu-id="aa322-264">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="aa322-265">V některých případech, kdy populární knihovny třetích stran nebo velký počet vývojářů závisí na interní rozhraní API, tyto změny nemusí být povoleny.</span><span class="sxs-lookup"><span data-stu-id="aa322-265">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="aa322-266">❓ **vyžaduje úsudek: Změna vnitřní implementace členského**</span><span class="sxs-lookup"><span data-stu-id="aa322-266">❓ **REQUIRES JUDGMENT: Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="aa322-267">Tyto změny jsou obecně povoleny, i když porušují soukromé reflexe.</span><span class="sxs-lookup"><span data-stu-id="aa322-267">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="aa322-268">V některých případech, kde kód zákazníka často závisí na soukromé reflexe nebo kde změna zavádí nežádoucí vedlejší účinky, tyto změny nemusí být povolena.</span><span class="sxs-lookup"><span data-stu-id="aa322-268">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="aa322-269">✔️ **povoleno: Zlepšení výkonu operace**</span><span class="sxs-lookup"><span data-stu-id="aa322-269">✔️ **ALLOWED: Improving the performance of an operation**</span></span>

   <span data-ttu-id="aa322-270">Schopnost změnit výkon operace je nezbytná, ale tyto změny mohou přerušit kód, který závisí na aktuální rychlosti operace.</span><span class="sxs-lookup"><span data-stu-id="aa322-270">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="aa322-271">To platí zejména pro kód, který závisí na časování asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="aa322-271">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="aa322-272">Změna výkonu by neměla mít žádný vliv na jiné chování daného rozhraní API; v opačném případě bude změna prolomena.</span><span class="sxs-lookup"><span data-stu-id="aa322-272">The performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="aa322-273">✔️ **povoleno: Nepřímo (a často nepříznivě) mění výkon operace**</span><span class="sxs-lookup"><span data-stu-id="aa322-273">✔️ **ALLOWED: Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="aa322-274">Není-li dotyčná změna z nějakého jiného důvodu kvalifikována jako porušení, je to přijatelné.</span><span class="sxs-lookup"><span data-stu-id="aa322-274">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="aa322-275">Často je třeba provést akce, které mohou zahrnovat další operace nebo které přidávají nové funkce.</span><span class="sxs-lookup"><span data-stu-id="aa322-275">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="aa322-276">To bude téměř vždy ovlivnit výkon, ale může být nezbytné, aby rozhraní API v otázce fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="aa322-276">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="aa322-277">❌**Zakázáno: Změna synchronního rozhraní API na asynchronní (a naopak)**</span><span class="sxs-lookup"><span data-stu-id="aa322-277">❌ **DISALLOWED: Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="aa322-278">Změny kódu</span><span class="sxs-lookup"><span data-stu-id="aa322-278">Code changes</span></span>

- <span data-ttu-id="aa322-279">✔️ **povoleno: Přidání [paramů](../../csharp/language-reference/keywords/params.md) do parametru**</span><span class="sxs-lookup"><span data-stu-id="aa322-279">✔️ **ALLOWED: Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="aa322-280">❌**Zakázáno: Změna [struktury](../../csharp/language-reference/builtin-types/struct.md) na [třídu](../../csharp/language-reference/keywords/class.md) a naopak**</span><span class="sxs-lookup"><span data-stu-id="aa322-280">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="aa322-281">❌**Zakázáno: Přidání [zaškrtnutého](../../csharp/language-reference/keywords/virtual.md) klíčového slova do bloku kódu**</span><span class="sxs-lookup"><span data-stu-id="aa322-281">❌ **DISALLOWED: Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="aa322-282">Tato změna může způsobit kód, který <xref:System.OverflowException> byl dříve spuštěn vyvolat a je nepřijatelné.</span><span class="sxs-lookup"><span data-stu-id="aa322-282">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="aa322-283">❌**Zakázáno: Odebrání [paramů](../../csharp/language-reference/keywords/params.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="aa322-283">❌ **DISALLOWED: Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="aa322-284">❌**Zakázáno: Změna pořadí, ve kterém jsou aktivovány události**</span><span class="sxs-lookup"><span data-stu-id="aa322-284">❌ **DISALLOWED: Changing the order in which events are fired**</span></span>

  <span data-ttu-id="aa322-285">Vývojáři mohou rozumně očekávat, že události se spálí ve stejném pořadí a kód vývojáře často závisí na pořadí, ve kterém jsou události aktivovány.</span><span class="sxs-lookup"><span data-stu-id="aa322-285">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="aa322-286">❌**Zakázáno: Odebrání vyvolání události u dané akce**</span><span class="sxs-lookup"><span data-stu-id="aa322-286">❌ **DISALLOWED: Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="aa322-287">❌**Zakázáno: Změna počtu, kolikrát se nazývají dané události.**</span><span class="sxs-lookup"><span data-stu-id="aa322-287">❌ **DISALLOWED: Changing the number of times given events are called**</span></span>

- <span data-ttu-id="aa322-288">❌**Zakázáno: Přidání <xref:System.FlagsAttribute> do typu výčtu**</span><span class="sxs-lookup"><span data-stu-id="aa322-288">❌ **DISALLOWED: Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>

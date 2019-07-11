---
title: Vyhodnotit změny způsobující chyby – .NET Core
description: Další informace o způsobech, ve kterém pokouší zachovat kompatibilitu mezi verzemi rozhraní .NET pro vývojáře v .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: c68a19b8b98a98bb9c64f5b9fa60b378935e6e93
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736555"
---
# <a name="evaluate-breaking-changes-in-net-core"></a><span data-ttu-id="9b374-103">Vyzkoušejte nejnovější změny v rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="9b374-103">Evaluate breaking changes in .NET Core</span></span>

<span data-ttu-id="9b374-104">V průběhu jeho historie se pokusil .NET udržují vysokou úroveň kompatibility z verze na verzi a mezi verzí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="9b374-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="9b374-105">Tento postup se opakuje na hodnotu true pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b374-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="9b374-106">I když novou technologii, která je nezávislá rozhraní .NET Framework lze považovat za .NET Core, dvou hlavních faktorech omezit schopnost .NET Core odchýlení od rozhraní .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9b374-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="9b374-107">Velký počet vývojáři původně vyvinutý nebo pokračovat ve vývoji aplikací využívajících rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b374-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="9b374-108">Očekávají konzistentní chování napříč implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="9b374-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="9b374-109">Projekty .NET standard knihovny umožňují vývojářům vytvářet knihovny, které se zaměřují společné rozhraní API, které sdílí .NET Core a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b374-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="9b374-110">Vývojáři očekávat, že knihovny použít v aplikaci .NET Core by se chovají stejně jako stejnou knihovnu použít v aplikaci .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b374-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="9b374-111">Vývojáři a informace o kompatibilitě mezi implementace .NET očekávat vysoké úrovně kompatibility ve verzích .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b374-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="9b374-112">Zejména by měl kód napsaný pro starší verzi .NET Core běžely na novější verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b374-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="9b374-113">Celá řada vývojářů ve skutečnosti očekávají, že nová rozhraní API v .NET Core nově vydané verze by měl být také kompatibilní s předběžnou verzí, ve kterých byly zavedeny těchto rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9b374-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="9b374-114">Tento článek popisuje kategorie kompatibility změny (nebo změny způsobující chyby) a způsob, ve kterém tým .NET vyhodnotí změny v každém z těchto kategorií.</span><span class="sxs-lookup"><span data-stu-id="9b374-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="9b374-115">Vysvětlení, jak tým .NET blíží možných nejnovějších změn je zvláště užitečné pro vývojáře, kteří jsou otevření žádosti o přijetí změn v [dotnet/corefx](https://github.com/dotnet/corefx) úložiště GitHub, které upravují chování stávajících rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9b374-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who are opening pull requests in the [dotnet/corefx](https://github.com/dotnet/corefx) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="9b374-116">Definice kategorií kompatibility, jako je například binární kompatibilitu a zpětnou kompatibilitu, naleznete v tématu [narušující změně kategorií](categories.md).</span><span class="sxs-lookup"><span data-stu-id="9b374-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="9b374-117">Následující části popisuje kategorie změny provedené v rozhraní API pro .NET Core a jejich dopad na kompatibilitu aplikací.</span><span class="sxs-lookup"><span data-stu-id="9b374-117">The following sections describes the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="9b374-118">Ikona ✔️ naznačuje, že konkrétní druh změn je povoleno, ❌ označuje, že je zakázané a ❓ označuje změnu, která můžou nebo nemusí být povolený.</span><span class="sxs-lookup"><span data-stu-id="9b374-118">The ✔️ icon indicates that a particular kind of change is allowed, ❌ indicates that it is disallowed, and  ❓ indicates a change that may or may not be allowed.</span></span> <span data-ttu-id="9b374-119">Změny v této poslední kategorii vyžadují posouzení a vyhodnocení jak předvídatelné, jasné a konzistentní předchozí chování byla.</span><span class="sxs-lookup"><span data-stu-id="9b374-119">Changes in this last category require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was.</span></span>

> [!NOTE]
> <span data-ttu-id="9b374-120">Kromě slouží jako vodítko, jak vyhodnotit změny knihovny .NET Core, vývojáře knihovny můžete také tato kritéria použít k vyhodnocení, změny v jejich knihovny cílené na více verzí a implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="9b374-120">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="9b374-121">Úpravy veřejný kontrakt</span><span class="sxs-lookup"><span data-stu-id="9b374-121">Modifications to the public contract</span></span>

<span data-ttu-id="9b374-122">Změny v této kategorii *upravit* veřejnou oblast typu.</span><span class="sxs-lookup"><span data-stu-id="9b374-122">Changes in this category *modify* the public surface area of a type.</span></span> <span data-ttu-id="9b374-123">Většina změn v této kategorii nejsou povoleny, protože porušují *zpětné kompatibility* (možnost aplikace, která byla vytvořena pomocí předchozí verze rozhraní API spouštět bez nutnosti rekompilace na novější verzi).</span><span class="sxs-lookup"><span data-stu-id="9b374-123">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="9b374-124">Typy</span><span class="sxs-lookup"><span data-stu-id="9b374-124">Types</span></span>

- <span data-ttu-id="9b374-125">**✔️ Odebrání implementaci rozhraní z typu, pokud rozhraní je již implementováno prostřednictvím základní typ**</span><span class="sxs-lookup"><span data-stu-id="9b374-125">**✔️ Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="9b374-126">**Přidání nové implementace rozhraní na typ ❓**</span><span class="sxs-lookup"><span data-stu-id="9b374-126">**❓ Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="9b374-127">To je přijatelné změnit, protože nepříznivě neovlivní stávající klienty.</span><span class="sxs-lookup"><span data-stu-id="9b374-127">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="9b374-128">Všechny změny na typ musí pracovat v rámci hranic přijatelné změny, které jsou zde definovány pro novou implementaci zůstat přijatelné.</span><span class="sxs-lookup"><span data-stu-id="9b374-128">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="9b374-129">Při přidávání rozhraní, které mají bezprostřední vliv na schopnost návrháře je nutné extrémně opatrní nebo spotřebovanými serializátor pro generování kódu nebo data, která nemůže být nižší úrovně.</span><span class="sxs-lookup"><span data-stu-id="9b374-129">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="9b374-130">Příkladem je <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9b374-130">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="9b374-131">**❓ Představujeme novou základní třídu**</span><span class="sxs-lookup"><span data-stu-id="9b374-131">**❓ Introducing a new base class**</span></span>

  <span data-ttu-id="9b374-132">Typ může být zavedeno v hierarchii mezi dva existující typy, pokud ji nemá žádné zavést nové [abstraktní](../../csharp/language-reference/keywords/abstract.md) členy nebo měnit sémantiku nebo chování existující typy.</span><span class="sxs-lookup"><span data-stu-id="9b374-132">A type can be introduced into an hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="9b374-133">Například v rozhraní .NET Framework 2.0 <xref:System.Data.Common.DbConnection> stal nové základní třída pro třídy <xref:System.Data.SqlClient.SqlConnection>, které dříve měly odvozena přímo z <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="9b374-133">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="9b374-134">**✔️ Přesunutí typu z jednoho sestavení do druhého**</span><span class="sxs-lookup"><span data-stu-id="9b374-134">**✔️ Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="9b374-135">Všimněte si, že *staré* sestavení musí být označeny pomocí <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> , která odkazuje na nové sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b374-135">Note that the *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="9b374-136">**✔️ Změna [struktura](../../csharp/language-reference/keywords/struct.md) typ, který `readonly struct` typu**</span><span class="sxs-lookup"><span data-stu-id="9b374-136">**✔️ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="9b374-137">Všimněte si, že změna `readonly struct` typ, který `struct` typ není povolený.</span><span class="sxs-lookup"><span data-stu-id="9b374-137">Note that changing a `readonly struct` type to a `struct` type is not allowed.</span></span>
  
- <span data-ttu-id="9b374-138">**✔️ Přidání [zapečetěné](../../csharp/language-reference/keywords/sealed.md) nebo [abstraktní](../../csharp/language-reference/keywords/abstract.md) – klíčové slovo do typu, pokud nejsou žádné *přístupné* konstruktory (veřejné nebo chráněné)**</span><span class="sxs-lookup"><span data-stu-id="9b374-138">**✔️ Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="9b374-139">**✔️ Rozbalení viditelnosti typu**</span><span class="sxs-lookup"><span data-stu-id="9b374-139">**✔️ Expanding the visibility of a type**</span></span>

- <span data-ttu-id="9b374-140">**❌ Změna oboru názvů nebo název typu**</span><span class="sxs-lookup"><span data-stu-id="9b374-140">**❌ Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="9b374-141">**❌ Přejmenování nebo odstranění veřejného typu**</span><span class="sxs-lookup"><span data-stu-id="9b374-141">**❌ Renaming or removing a public type**</span></span>

   <span data-ttu-id="9b374-142">Tím je prolomen veškerý kód, který používá typ přejmenovaných nebo odebrané.</span><span class="sxs-lookup"><span data-stu-id="9b374-142">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="9b374-143">**Změna základního typu výčtu ❌**</span><span class="sxs-lookup"><span data-stu-id="9b374-143">**❌ Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="9b374-144">Toto je za kompilace a chování rozbíjející změny, stejně jako binární zásadní změnu, která může být argumenty atributu nelze analyzovat.</span><span class="sxs-lookup"><span data-stu-id="9b374-144">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="9b374-145">**Typ, který byl dříve nezapečetěné zapečetění ❌**</span><span class="sxs-lookup"><span data-stu-id="9b374-145">**❌ Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="9b374-146">**Přidání rozhraní ke sadu základních typů rozhraní ❌**</span><span class="sxs-lookup"><span data-stu-id="9b374-146">**❌ Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="9b374-147">Pokud rozhraní implementuje rozhraní, které dříve neimplementovala, všechny typy, které implementované původní verzi rozhraní jsou přerušená.</span><span class="sxs-lookup"><span data-stu-id="9b374-147">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="9b374-148">**❓ Odebrání sady základní třídy nebo rozhraní ze sady implementovaných rozhraní třídy**</span><span class="sxs-lookup"><span data-stu-id="9b374-148">**❓ Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="9b374-149">Existuje jedna výjimka z pravidla pro odebrání rozhraní: můžete přidat implementaci rozhraní, který je odvozen z rozhraní odebrané.</span><span class="sxs-lookup"><span data-stu-id="9b374-149">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="9b374-150">Například můžete odebrat <xref:System.IDisposable> Pokud tento typ nebo rozhraní nyní implementuje <xref:System.ComponentModel.IComponent>, která implementuje <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="9b374-150">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="9b374-151">**❌ Změna `readonly struct` typ, který [struktura](../../csharp/language-reference/keywords/struct.md) typu**</span><span class="sxs-lookup"><span data-stu-id="9b374-151">**❌ Changing a `readonly struct` type to a [struct](../../csharp/language-reference/keywords/struct.md) type**</span></span>

  <span data-ttu-id="9b374-152">Všimněte si, že změna `struct` typ, který `readonly struct` typ je povolený.</span><span class="sxs-lookup"><span data-stu-id="9b374-152">Note that the change of a `struct` type to a `readonly struct` type is allowed.</span></span>

- <span data-ttu-id="9b374-153">**❌ Změna [struktura](../../csharp/language-reference/keywords/struct.md) typ, který `ref struct` typ a naopak**</span><span class="sxs-lookup"><span data-stu-id="9b374-153">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="9b374-154">**❌ Snižuje viditelnost typu**</span><span class="sxs-lookup"><span data-stu-id="9b374-154">**❌ Reducing the visibility of a type**</span></span>

   <span data-ttu-id="9b374-155">Viditelnost typu je však povoleno.</span><span class="sxs-lookup"><span data-stu-id="9b374-155">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="9b374-156">Členové</span><span class="sxs-lookup"><span data-stu-id="9b374-156">Members</span></span>

- <span data-ttu-id="9b374-157">**Rozbalení viditelnost člena, který není ✔️ [virtuální](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="9b374-157">**✔️ Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="9b374-158">**✔️ Přidání abstraktní člen veřejný typ, který nemá žádné *přístupné* konstruktory (veřejné nebo chráněné), nebo typ je [zapečetěné](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="9b374-158">**✔️ Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="9b374-159">Ale přidání abstraktní člen na typ, který má přístupné konstruktory (veřejné nebo chráněné) a není `sealed` není povolený.</span><span class="sxs-lookup"><span data-stu-id="9b374-159">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="9b374-160">**✔️ Omezení viditelnost [chráněné](../../csharp/language-reference/keywords/protected.md) členský typ nemá žádné přístupné konstruktory (veřejné nebo chráněné), nebo je typ [zapečetěné](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="9b374-160">**✔️ Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="9b374-161">**✔️ Přesunutí člena do výše v hierarchii než ze kterého byla odebrána typ třídy**</span><span class="sxs-lookup"><span data-stu-id="9b374-161">**✔️ Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="9b374-162">**✔️ Přidání nebo odebrání přepsání**</span><span class="sxs-lookup"><span data-stu-id="9b374-162">**✔️ Adding or removing an override**</span></span>

  <span data-ttu-id="9b374-163">Mějte na paměti, Představujeme přepsání může způsobit předchozí spotřebitele mají přeskočit při volání metody přepsání [základní](../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="9b374-163">Note that introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="9b374-164">**✔️ Přidáním konstruktoru do třídy, spolu s výchozí (bezparametrový) konstruktor, pokud třída již dříve měli žádné konstruktory**</span><span class="sxs-lookup"><span data-stu-id="9b374-164">**✔️ Adding a constructor to a class, along with a default (parameterless) constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="9b374-165">Ale přidáním konstruktoru do třídy, které dříve měly žádné konstruktory *bez* přidání konstruktor bez parametrů není povoleno.</span><span class="sxs-lookup"><span data-stu-id="9b374-165">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="9b374-166">**✔️ Změna člena z [abstraktní](../../csharp/language-reference/keywords/abstract.md) k [virtuální](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="9b374-166">**✔️ Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="9b374-167">**✔️ Změny z `ref readonly` k `ref` návratovou hodnotu (s výjimkou virtuální metody nebo rozhraní)**</span><span class="sxs-lookup"><span data-stu-id="9b374-167">**✔️ Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="9b374-168">**✔️ Odebrání [jen pro čtení](../../csharp/language-reference/keywords/readonly.md) z pole, pokud typ statického pole je typu proměnlivé hodnoty**</span><span class="sxs-lookup"><span data-stu-id="9b374-168">**✔️ Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="9b374-169">**Volání nové události, která nebyla dříve definovali ✔️**</span><span class="sxs-lookup"><span data-stu-id="9b374-169">**✔️ Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="9b374-170">**Přidání nového pole instance na typ ❓**</span><span class="sxs-lookup"><span data-stu-id="9b374-170">**❓ Adding a new instance field to a type**</span></span>

   <span data-ttu-id="9b374-171">Tato změna má vliv na serializace.</span><span class="sxs-lookup"><span data-stu-id="9b374-171">This change impacts serialization.</span></span>

- <span data-ttu-id="9b374-172">**❌ Přejmenování nebo odstranění veřejný člen nebo parametr**</span><span class="sxs-lookup"><span data-stu-id="9b374-172">**❌ Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="9b374-173">Tím je prolomen veškerý kód, který používá přejmenovaných nebo odebraný člen nebo parametr.</span><span class="sxs-lookup"><span data-stu-id="9b374-173">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="9b374-174">Všimněte si, že to zahrnuje odebrání nebo přejmenování getter nebo setter z vlastnosti, jakož i přejmenování nebo odstranění výčet členů.</span><span class="sxs-lookup"><span data-stu-id="9b374-174">Note that this includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="9b374-175">**Přidání člena do rozhraní ❌**</span><span class="sxs-lookup"><span data-stu-id="9b374-175">**❌ Adding a member to an interface**</span></span>

- <span data-ttu-id="9b374-176">**Změna hodnoty veřejný člen nebo konstanta výčtu ❌**</span><span class="sxs-lookup"><span data-stu-id="9b374-176">**❌ Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="9b374-177">**❌ Změnou typu vlastnosti, pole, parametr nebo návratovou hodnotu**</span><span class="sxs-lookup"><span data-stu-id="9b374-177">**❌ Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="9b374-178">**❌ Přidání, odebrání nebo změně pořadí parametrů**</span><span class="sxs-lookup"><span data-stu-id="9b374-178">**❌ Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="9b374-179">**❌ Přidání nebo odebrání [v](../../csharp/language-reference/keywords/in.md), [si](../../csharp/language-reference/keywords/out.md) , nebo [ref](../../csharp/language-reference/keywords/ref.md) – klíčové slovo z parametru**</span><span class="sxs-lookup"><span data-stu-id="9b374-179">**❌ Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="9b374-180">**❌ Přejmenování parametru (včetně změna jeho velikosti písmen)**</span><span class="sxs-lookup"><span data-stu-id="9b374-180">**❌ Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="9b374-181">To je považováno za rozbíjející dva důvody:</span><span class="sxs-lookup"><span data-stu-id="9b374-181">This is considered breaking for two reasons:</span></span>
  
  - <span data-ttu-id="9b374-182">To naruší s pozdní vazbou scénářů, jako je pozdní vazba funkce v jazyce Visual Basic a [dynamické](../../csharp/language-reference/keywords/dynamic.md) v C#.</span><span class="sxs-lookup"><span data-stu-id="9b374-182">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/keywords/dynamic.md) in C#.</span></span>
  
  - <span data-ttu-id="9b374-183">To naruší [zdroje kompatibility](categories.md#source-compatibility) když vývojáři [pojmenované argumenty](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span><span class="sxs-lookup"><span data-stu-id="9b374-183">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="9b374-184">**❌ Změny z `ref` vracet hodnotu `ref readonly` návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="9b374-184">**❌ Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="9b374-185">**❌️ Změny z `ref readonly` k `ref` návratová hodnota na virtuální metody nebo rozhraní**</span><span class="sxs-lookup"><span data-stu-id="9b374-185">**❌️ Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="9b374-186">**❌ Přidání nebo odebrání [abstraktní](../../csharp/language-reference/keywords/abstract.md) od člena**</span><span class="sxs-lookup"><span data-stu-id="9b374-186">**❌ Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="9b374-187">**❌ Odebírá [virtuální](../../csharp/language-reference/keywords/virtual.md) – klíčové slovo z člena**</span><span class="sxs-lookup"><span data-stu-id="9b374-187">**❌ Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="9b374-188">To často není k zásadní změně protože C# kompilátor může vygenerovat [Call, callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) pokyny k volání nevirtuální metody (`callvirt` provádí kontrolu hodnot null, zatímco nebude normální volání ), toto chování není konstantní z několika důvodů:</span><span class="sxs-lookup"><span data-stu-id="9b374-188">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="9b374-189">C#není pouze jazyk, který cílí na .NET.</span><span class="sxs-lookup"><span data-stu-id="9b374-189">C# is not the only language that .NET targets.</span></span>
  
  - <span data-ttu-id="9b374-190">C# Kompilátoru stále pokusí optimalizovat `callvirt` normální volání pokaždé, když se do cílové metody je nevirtuální a není pravděpodobně null (například pro metodu prostřednictvím [?. operátor šíření hodnoty null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span><span class="sxs-lookup"><span data-stu-id="9b374-190">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>
  
  <span data-ttu-id="9b374-191">Provádění virtuální metoda znamená, že uživatelský kód často skončili byste volání bez prakticky.</span><span class="sxs-lookup"><span data-stu-id="9b374-191">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="9b374-192">**❌ Přidání [virtuální](../../csharp/language-reference/keywords/virtual.md) – klíčové slovo ke členovi**</span><span class="sxs-lookup"><span data-stu-id="9b374-192">**❌ Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="9b374-193">**❌, že virtuální člen abstraktní**</span><span class="sxs-lookup"><span data-stu-id="9b374-193">**❌ Making a virtual member abstract**</span></span>

  <span data-ttu-id="9b374-194">A [virtuální člen](../../csharp/language-reference/keywords/virtual.md) obsahuje implementace metody, které *může být* přepsána odvozenou třídou.</span><span class="sxs-lookup"><span data-stu-id="9b374-194">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="9b374-195">[Abstraktní člen](../../csharp/language-reference/keywords/abstract.md) poskytuje implementaci a *musí být* přepsat.</span><span class="sxs-lookup"><span data-stu-id="9b374-195">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="9b374-196">**❌ Přidání abstraktní člen veřejný typ, který má přístupné konstruktory (veřejné nebo chráněné) a že není [zapečetěné](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="9b374-196">**❌ Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="9b374-197">**❌ Přidání nebo odebrání [statické](../../csharp/language-reference/keywords/static.md) – klíčové slovo z člena**</span><span class="sxs-lookup"><span data-stu-id="9b374-197">**❌ Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="9b374-198">**Přidání přetížení, které vylučuje existující přetížení a definuje různé chování ❌**</span><span class="sxs-lookup"><span data-stu-id="9b374-198">**❌ Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="9b374-199">Tím je prolomen existující klienti, kteří byly vázána na předchozí přetížení.</span><span class="sxs-lookup"><span data-stu-id="9b374-199">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="9b374-200">Například pokud třída má jednu verzi metody, která přijímá <xref:System.UInt32>, stávající příjemce se úspěšně vytvořit vazbu tohoto přetížení při předávání <xref:System.Int32> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9b374-200">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="9b374-201">Ale pokud přidáte přetížení, která přijímá <xref:System.Int32>při opětovné kompilaci nebo pomocí pozdní vazby, kompilátor nyní vytvoří vazbu nové přetížení.</span><span class="sxs-lookup"><span data-stu-id="9b374-201">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="9b374-202">Pokud různé chování vyplývá, je to zásadní změnu.</span><span class="sxs-lookup"><span data-stu-id="9b374-202">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="9b374-203">**❌ Přidáním konstruktoru do třídy, které dříve měly žádný konstruktor bez přidání konstruktor bez parametrů**</span><span class="sxs-lookup"><span data-stu-id="9b374-203">**❌ Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="9b374-204">**❌️ Přidání [jen pro čtení](../../csharp/language-reference/keywords/readonly.md) na pole**</span><span class="sxs-lookup"><span data-stu-id="9b374-204">**❌️ Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="9b374-205">**❌ Snižuje viditelnost člena**</span><span class="sxs-lookup"><span data-stu-id="9b374-205">**❌ Reducing the visibility of a member**</span></span>

   <span data-ttu-id="9b374-206">Jedná se o snižuje viditelnost [chráněné](../../csharp/language-reference/keywords/protected.md) člen, když nejsou *přístupné* konstruktory (veřejné nebo chráněné) a typ je *není* [ zapečetěné](../../csharp/language-reference/keywords/sealed.md).</span><span class="sxs-lookup"><span data-stu-id="9b374-206">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (public or protected) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="9b374-207">Pokud to není tento případ, snižuje viditelnost chráněný člen je povolený.</span><span class="sxs-lookup"><span data-stu-id="9b374-207">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="9b374-208">Všimněte si, že není povoleno zvýšení viditelnosti člena.</span><span class="sxs-lookup"><span data-stu-id="9b374-208">Note that increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="9b374-209">**❌ Změnu typu člena**</span><span class="sxs-lookup"><span data-stu-id="9b374-209">**❌ Changing the type of a member**</span></span>

   <span data-ttu-id="9b374-210">Návratová hodnota metody nebo typ pole nebo vlastnost nelze upravovat.</span><span class="sxs-lookup"><span data-stu-id="9b374-210">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="9b374-211">Například podpis metody, která se vrátí <xref:System.Object> nelze změnit na vrácení <xref:System.String>, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="9b374-211">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="9b374-212">**❌ Přidání pole do struktury, které dříve měly žádný stav**</span><span class="sxs-lookup"><span data-stu-id="9b374-212">**❌ Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="9b374-213">Pravidla jednoznačného přiřazení umožňují použití neinicializované proměnné tak dlouho, dokud bezstavové struktura je typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="9b374-213">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="9b374-214">Pokud struktura stavové, kód může skončit s neinicializovaná data.</span><span class="sxs-lookup"><span data-stu-id="9b374-214">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="9b374-215">Toto je potenciálně zdroj dopadem na dřívější kód a binární narušující změna.</span><span class="sxs-lookup"><span data-stu-id="9b374-215">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="9b374-216">**❌ Ohlásí, existující událost v případě, že se nikdy vyvolala před**</span><span class="sxs-lookup"><span data-stu-id="9b374-216">**❌ Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="9b374-217">Změny chování</span><span class="sxs-lookup"><span data-stu-id="9b374-217">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="9b374-218">Sestavení</span><span class="sxs-lookup"><span data-stu-id="9b374-218">Assemblies</span></span>

- <span data-ttu-id="9b374-219">**✔️ Zajištění přenositelnosti sestavení, když stejných platformách jsou stále podporovány.**</span><span class="sxs-lookup"><span data-stu-id="9b374-219">**✔️ Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="9b374-220">**Změna názvu sestavení ❌**</span><span class="sxs-lookup"><span data-stu-id="9b374-220">**❌ Changing the name of an assembly**</span></span>
- <span data-ttu-id="9b374-221">**❌ Změna veřejný klíč sestavení**</span><span class="sxs-lookup"><span data-stu-id="9b374-221">**❌ Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="9b374-222">Vlastnosti, pole, parametry a návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="9b374-222">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="9b374-223">**✔️ Změnou hodnoty vlastnosti, pole, návratová hodnota nebo [si](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr více odvozený typ**</span><span class="sxs-lookup"><span data-stu-id="9b374-223">**✔️ Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="9b374-224">Například metoda, která vrací typ <xref:System.Object> můžete vrátit <xref:System.String> instance.</span><span class="sxs-lookup"><span data-stu-id="9b374-224">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="9b374-225">(Však podpis metody nelze změnit.)</span><span class="sxs-lookup"><span data-stu-id="9b374-225">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="9b374-226">**✔️ Zvýšení rozsahu přijaté hodnoty pro vlastnost nebo parametr, pokud člen není [virtuální](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="9b374-226">**✔️ Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="9b374-227">Všimněte si, že při rozsah hodnot, které může být předán metodě nebo člen vrací můžete rozšířit, nelze typ parametru nebo člen.</span><span class="sxs-lookup"><span data-stu-id="9b374-227">Note that while the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="9b374-228">Například když hodnoty předané metodě můžete rozšířit z 0-124 na 0 – 255, typ parametru nelze změnit z <xref:System.Byte> k <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="9b374-228">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="9b374-229">**❌ Zvýšení rozsahu přijaté hodnoty pro vlastnost nebo parametr, pokud je člen [virtuální](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="9b374-229">**❌ Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="9b374-230">Tato změna přeruší stávající přepsaného členy, které nebude fungovat správně pro delší rozsah hodnot.</span><span class="sxs-lookup"><span data-stu-id="9b374-230">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="9b374-231">**❌ Snížení rozsah platných hodnot pro vlastnost nebo parametr**</span><span class="sxs-lookup"><span data-stu-id="9b374-231">**❌ Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="9b374-232">**Zvýšení rozsahu ❌ vrácené hodnoty pro vlastnosti, pole, návratová hodnota nebo [si](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**</span><span class="sxs-lookup"><span data-stu-id="9b374-232">**❌ Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="9b374-233">**❌ Změna vrácených hodnot pro vlastnosti, pole, metoda návratovou hodnotu, nebo [si](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**</span><span class="sxs-lookup"><span data-stu-id="9b374-233">**❌ Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="9b374-234">**Změna výchozí hodnoty vlastnosti, pole nebo parametr ❌**</span><span class="sxs-lookup"><span data-stu-id="9b374-234">**❌ Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="9b374-235">**❌ Změna přesnosti číselná návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="9b374-235">**❌ Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="9b374-236">**Změna ❓ A parsování vstupu a vyvolání nové výjimky (i v případě, že analýza chování není uveden v dokumentaci**</span><span class="sxs-lookup"><span data-stu-id="9b374-236">**❓ A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="9b374-237">Výjimky</span><span class="sxs-lookup"><span data-stu-id="9b374-237">Exceptions</span></span>

- <span data-ttu-id="9b374-238">**✔️ Vyvolání výjimky více odvozený než existující výjimky**</span><span class="sxs-lookup"><span data-stu-id="9b374-238">**✔️ Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="9b374-239">Protože nová výjimka je podtřídou existující výjimky, pokračuje v předchozí kód zpracování výjimek pro zpracování výjimky.</span><span class="sxs-lookup"><span data-stu-id="9b374-239">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="9b374-240">Metody vytváření a načítání jazykové verze v rozhraní .NET Framework 4, například začal vyvolávat <xref:System.Globalization.CultureNotFoundException> místo <xref:System.ArgumentException> Pokud jazykové verze se nenašla.</span><span class="sxs-lookup"><span data-stu-id="9b374-240">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="9b374-241">Protože <xref:System.Globalization.CultureNotFoundException> je odvozena z <xref:System.ArgumentException>, to je přijatelné změnit.</span><span class="sxs-lookup"><span data-stu-id="9b374-241">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="9b374-242">**Vyvolání více specifické výjimky než ✔️ <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span><span class="sxs-lookup"><span data-stu-id="9b374-242">**✔️ Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="9b374-243">**Došlo k výjimce, která se považuje za neopravitelné ✔️**</span><span class="sxs-lookup"><span data-stu-id="9b374-243">**✔️ Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="9b374-244">Neopravitelné výjimky by neměly být zachycovány, ale místo toho by měla být zpracovány vysoké úrovně obslužné rutiny catch – to všechno.</span><span class="sxs-lookup"><span data-stu-id="9b374-244">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="9b374-245">Uživatelé se tedy, že kód, který zachytává tyto explicitní výjimky.</span><span class="sxs-lookup"><span data-stu-id="9b374-245">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="9b374-246">Neopravitelné výjimky jsou:</span><span class="sxs-lookup"><span data-stu-id="9b374-246">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="9b374-247">**✔️ Vyvolání nové výjimky novou cestu kódu**</span><span class="sxs-lookup"><span data-stu-id="9b374-247">**✔️ Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="9b374-248">Výjimka musíte použít pouze pro nový kód – cestu, který je proveden pomocí nové hodnoty parametru nebo stav, a existující kód, který nemůže provést, který cílí na předchozí verzi.</span><span class="sxs-lookup"><span data-stu-id="9b374-248">The exception must apply only to a new code-path which is executed with new parameter values or state, and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="9b374-249">**Odebrání výjimky umožňující robustnější chování nebo nové scénáře ✔️**</span><span class="sxs-lookup"><span data-stu-id="9b374-249">**✔️ Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="9b374-250">Například `Divide` metodu, která dříve pouze kladné hodnoty zpracovat a došlo <xref:System.ArgumentOutOfRangeException> jinak je změnit, aby bez vyvolání výjimky nepodporuje záporné i kladné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9b374-250">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="9b374-251">**✔️ Změnu textu chybovou zprávu**</span><span class="sxs-lookup"><span data-stu-id="9b374-251">**✔️ Changing the text of an error message**</span></span>

  <span data-ttu-id="9b374-252">Vývojáři, neměli byste tedy spoléhat na textu chybové zprávy, které také změní na základě jazykové verze uživatele.</span><span class="sxs-lookup"><span data-stu-id="9b374-252">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="9b374-253">**❌ Došlo k výjimce ve všech ostatních případech není uvedené výš**</span><span class="sxs-lookup"><span data-stu-id="9b374-253">**❌ Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="9b374-254">**Odebrání výjimky ve všech ostatních případech není uvedené výš ❌**</span><span class="sxs-lookup"><span data-stu-id="9b374-254">**❌ Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="9b374-255">Atributy</span><span class="sxs-lookup"><span data-stu-id="9b374-255">Attributes</span></span>

- <span data-ttu-id="9b374-256">**Změna hodnoty atributu, který je ✔️ *není* pozorovat**</span><span class="sxs-lookup"><span data-stu-id="9b374-256">**✔️ Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="9b374-257">**❌ Změnit hodnotu atributu, který *je* pozorovat**</span><span class="sxs-lookup"><span data-stu-id="9b374-257">**❌ Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="9b374-258">**❓ Odebrat atribut**</span><span class="sxs-lookup"><span data-stu-id="9b374-258">**❓ Removing an attribute**</span></span>

  <span data-ttu-id="9b374-259">Ve většině případů odebrání atributu (například <xref:System.NonSerializedAttribute>) je zásadní změnu.</span><span class="sxs-lookup"><span data-stu-id="9b374-259">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="9b374-260">Podpora platforem</span><span class="sxs-lookup"><span data-stu-id="9b374-260">Platform support</span></span>

- <span data-ttu-id="9b374-261">**Podporuje operace na platformě, která se dříve podporovaly ✔️**</span><span class="sxs-lookup"><span data-stu-id="9b374-261">**✔️ Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="9b374-262">**❌ Není podpory nebo nyní vyžadování konkrétního service pack pro operace, který byl dříve podporován na platformě**</span><span class="sxs-lookup"><span data-stu-id="9b374-262">**❌ Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="9b374-263">Vnitřní implementace změny</span><span class="sxs-lookup"><span data-stu-id="9b374-263">Internal implementation changes</span></span>

- <span data-ttu-id="9b374-264">**❓ Změna útoku na vnitřní typ**</span><span class="sxs-lookup"><span data-stu-id="9b374-264">**❓ Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="9b374-265">Tyto změny jsou obecně povoleny, i když jsou přerušit privátní reflexe.</span><span class="sxs-lookup"><span data-stu-id="9b374-265">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="9b374-266">V některých případech, kdy Oblíbené knihovny třetích stran nebo velký počet vývojáře závisí na interních rozhraních API, nemusí být povolený tyto změny.</span><span class="sxs-lookup"><span data-stu-id="9b374-266">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="9b374-267">**❓ Změna vnitřní implementace členu**</span><span class="sxs-lookup"><span data-stu-id="9b374-267">**❓ Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="9b374-268">Tyto změny jsou obecně povoleny, i když jsou přerušit privátní reflexe.</span><span class="sxs-lookup"><span data-stu-id="9b374-268">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="9b374-269">V některých případech, pokud kód zákazníka často závisí na reflexi privátní nebo kde změna představuje nežádoucí vedlejší účinky, nemusí být povolený tyto změny.</span><span class="sxs-lookup"><span data-stu-id="9b374-269">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="9b374-270">**Zlepšení výkonu operace ✔️**</span><span class="sxs-lookup"><span data-stu-id="9b374-270">**✔️ Improving the performance of an operation**</span></span>

   <span data-ttu-id="9b374-271">Schopnost upravovat výkonu operace je nezbytné, ale tyto změny může dojít k narušení kódu, která závisí na aktuální rychlost operace.</span><span class="sxs-lookup"><span data-stu-id="9b374-271">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="9b374-272">To platí zejména pro kód, který závisí na načasování asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="9b374-272">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="9b374-273">Všimněte si, že změna výkonu by neměla mít žádný vliv na jiné chování rozhraní API dotyčný; v opačném případě se zásadní změnu.</span><span class="sxs-lookup"><span data-stu-id="9b374-273">Note that the performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="9b374-274">**✔️ Nepřímo (a často nepříznivě) Změna výkonu operace**</span><span class="sxs-lookup"><span data-stu-id="9b374-274">**✔️ Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="9b374-275">Pokud se dané změny není kategorizována jako zásadní nějakého jiného důvodu, je to přijatelné.</span><span class="sxs-lookup"><span data-stu-id="9b374-275">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="9b374-276">Často akce nezbytné mají být provedeny, který může obsahovat další operace nebo přidá nové funkce.</span><span class="sxs-lookup"><span data-stu-id="9b374-276">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="9b374-277">To bude téměř vždy mít vliv na výkon, ale může být nezbytné, aby rozhraní API ve funkci dotaz podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="9b374-277">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="9b374-278">**❌ Změna synchronního rozhraní API na asynchronní (a naopak)**</span><span class="sxs-lookup"><span data-stu-id="9b374-278">**❌ Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="9b374-279">Změny kódu</span><span class="sxs-lookup"><span data-stu-id="9b374-279">Code changes</span></span>

- <span data-ttu-id="9b374-280">**✔️ Přidání [params](../../csharp/language-reference/keywords/params.md) na parametr**</span><span class="sxs-lookup"><span data-stu-id="9b374-280">**✔️ Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="9b374-281">**❌ Změna [struktura](../../csharp/language-reference/keywords/struct.md) k [třídy](../../csharp/language-reference/keywords/class.md) a naopak**</span><span class="sxs-lookup"><span data-stu-id="9b374-281">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="9b374-282">**❌ Přidání [zaškrtnutí](../../csharp/language-reference/keywords/virtual.md) – klíčové slovo k bloku kódu**</span><span class="sxs-lookup"><span data-stu-id="9b374-282">**❌ Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="9b374-283">Tato změna může způsobit, že kód, který dříve provedený vyvolání <xref:System.OverflowException> a nemůže být přijata.</span><span class="sxs-lookup"><span data-stu-id="9b374-283">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="9b374-284">**❌ Odebrání [params](../../csharp/language-reference/keywords/params.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="9b374-284">**❌ Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="9b374-285">**Změna pořadí, ve kterém jsou vyvolávány události ❌**</span><span class="sxs-lookup"><span data-stu-id="9b374-285">**❌ Changing the order in which events are fired**</span></span>

  <span data-ttu-id="9b374-286">Vývojáři můžou očekávat rozumně události, která se aktivuje ve stejném pořadí a kód vývojáře často závisí na pořadí, ve kterém jsou vyvolávány události.</span><span class="sxs-lookup"><span data-stu-id="9b374-286">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="9b374-287">**❌ Odebrání vyvolání události pro danou akci**</span><span class="sxs-lookup"><span data-stu-id="9b374-287">**❌ Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="9b374-288">**Jsou volány ❌ změna počet, kolikrát daný události**</span><span class="sxs-lookup"><span data-stu-id="9b374-288">**❌ Changing the number of times given events are called**</span></span>

- <span data-ttu-id="9b374-289">**❌ Přidání <xref:System.FlagsAttribute> na typ výčtu**</span><span class="sxs-lookup"><span data-stu-id="9b374-289">**❌ Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>

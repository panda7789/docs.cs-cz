---
title: C# Správa verzí – Průvodce v C#
description: Pochopení principu správy verzí v C# a .NET
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 949b7414116169cada62b48392f37809f26d7ff9
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970237"
---
# <a name="versioning-in-c"></a><span data-ttu-id="693d5-103">Správa verzí v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="693d5-103">Versioning in C#</span></span> #

<span data-ttu-id="693d5-104">V tomto kurzu se dozvíte, jaké správy verzí znamená, že v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="693d5-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="693d5-105">Dozvíte se víc i faktory vzít v úvahu při správy verzí knihovny, jakož i upgrade na novou verzi knihovny.</span><span class="sxs-lookup"><span data-stu-id="693d5-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of the a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="693d5-106">Vytváření knihovny</span><span class="sxs-lookup"><span data-stu-id="693d5-106">Authoring Libraries</span></span>

<span data-ttu-id="693d5-107">Jako vývojář, který byl vytvořen knihovny .NET pro veřejně přístupný, když jste většinu pravděpodobně byl v situacích, kdy máte zavádět nové aktualizace.</span><span class="sxs-lookup"><span data-stu-id="693d5-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="693d5-108">Jak přejít o tomto procesu hrají podle musíte zajistit, že je jednoduchý přechod z existujícího kódu na novou verzi knihovny.</span><span class="sxs-lookup"><span data-stu-id="693d5-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="693d5-109">Tady je několik věcí, které je třeba zvážit při vytváření nové vydané verze:</span><span class="sxs-lookup"><span data-stu-id="693d5-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="693d5-110">Semantic Versioning</span><span class="sxs-lookup"><span data-stu-id="693d5-110">Semantic Versioning</span></span>

<span data-ttu-id="693d5-111">[Sémantické správy verzí](http://semver.org/) (SemVer zkráceně) je zásady vytváření názvů u verze knihovny místo konkrétní verze události.</span><span class="sxs-lookup"><span data-stu-id="693d5-111">[Semantic versioning](http://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="693d5-112">V ideálním případě informací o verzi, poskytnete své knihovny by měly pomoci vývojářům zjistit informace o kompatibilitě s jejich projekty, které využívají starší verze, která stejné knihovny.</span><span class="sxs-lookup"><span data-stu-id="693d5-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="693d5-113">Nejzákladnější přístup k SemVer je formát 3 komponenty `MAJOR.MINOR.PATCH`, kde:</span><span class="sxs-lookup"><span data-stu-id="693d5-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

* <span data-ttu-id="693d5-114">`MAJOR` se zvýší, když provedete změny nekompatibilní rozhraní API</span><span class="sxs-lookup"><span data-stu-id="693d5-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
* <span data-ttu-id="693d5-115">`MINOR` se zvýší, když přidáte funkci způsobem zpětně kompatibilní</span><span class="sxs-lookup"><span data-stu-id="693d5-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
* <span data-ttu-id="693d5-116">`PATCH` se zvýší, když provedete zpětně kompatibilní opravy chyb</span><span class="sxs-lookup"><span data-stu-id="693d5-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="693d5-117">Existují také způsoby, jak určit jiné scénáře, jako jsou předběžné verze atd. při použití informací o verzi na knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="693d5-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="693d5-118">Zpětné kompatibility</span><span class="sxs-lookup"><span data-stu-id="693d5-118">Backwards Compatibility</span></span>

<span data-ttu-id="693d5-119">Jak vydáním nové verze knihovny zpětné kompatibility s předchozími verzemi bude pravděpodobně mezi hlavní priority.</span><span class="sxs-lookup"><span data-stu-id="693d5-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="693d5-120">Zdroj kompatibilní s předchozí verzí, pokud kód, který závisí na předchozí verzi, při nové kompilaci neúspěchu v nové verzi je nová verze knihovny.</span><span class="sxs-lookup"><span data-stu-id="693d5-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="693d5-121">Pokud aplikace, která závisí na předchozí verzi aplikace můžou bez rekompilace, pracovat s novou verzi, je nová verze knihovny binární kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="693d5-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="693d5-122">Tady je pár věcí k uvážení při pokusu o zachování zpětné kompatibility se staršími verzemi knihovny:</span><span class="sxs-lookup"><span data-stu-id="693d5-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

* <span data-ttu-id="693d5-123">Virtuální metody: Když nastavíte virtuální metoda nevirtuální ve vaší novou verzi, znamená to, že projekty, které potlačí tuto metodu bude muset aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="693d5-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="693d5-124">To je obrovská rozbíjející změny a se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="693d5-124">This is a huge breaking change and is strongly discouraged.</span></span>
* <span data-ttu-id="693d5-125">Podpisy metod: při aktualizaci chování metoda vyžaduje, abyste změňte její signaturu tak dobře, měli byste místo toho vytvořit přetížení tak, aby kód volání do metody budou i nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="693d5-125">Method signatures: When updating a method behaviour requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="693d5-126">Vždy můžete pracovat s starý podpis metody, chcete-li volat nový podpis metody tak, aby zůstala konzistentní implementaci.</span><span class="sxs-lookup"><span data-stu-id="693d5-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
* <span data-ttu-id="693d5-127">[Zastaralé atribut](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Tento atribut v kódu můžete použít k určení třídy nebo členy třídy, které jsou zastaralé a pravděpodobně odebrán v budoucích verzích.</span><span class="sxs-lookup"><span data-stu-id="693d5-127">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span>
<span data-ttu-id="693d5-128">Tím se zajistí, že vývojáři využívající knihovnu lépe připraveni rozbíjející změny.</span><span class="sxs-lookup"><span data-stu-id="693d5-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
* <span data-ttu-id="693d5-129">Volitelné argumenty metody: Kdy provést povinné argumenty dříve volitelné metody nebo změnit výchozí hodnoty a veškerý kód, který neposkytuje tyto argumenty budou potřeba aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="693d5-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>
> [!NOTE]
> <span data-ttu-id="693d5-130">Provádění povinné argumenty volitelné by měl mít velmi malý vliv, zejména v případě, že ho nedojde ke změně chování metody.</span><span class="sxs-lookup"><span data-stu-id="693d5-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behaviour.</span></span>

<span data-ttu-id="693d5-131">Tím snadněji provedete to pro vaše uživatele pro upgrade na novou verzi knihovny, tím pravděpodobnější, že se bude upgradovat dřív.</span><span class="sxs-lookup"><span data-stu-id="693d5-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="693d5-132">Konfigurační soubor aplikace</span><span class="sxs-lookup"><span data-stu-id="693d5-132">Application Configuration File</span></span>

<span data-ttu-id="693d5-133">Jako vývojář .NET existuje velmi vysoká pravděpodobnost, kterým jste se setkali [ `app.config` soubor](../framework/configure-apps/file-schema/index.md) součástí většinu typů projektu.</span><span class="sxs-lookup"><span data-stu-id="693d5-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="693d5-134">Tento jednoduchý konfigurační soubor můžete urazily dlouhou cestu do zlepšení zavedení nové aktualizace.</span><span class="sxs-lookup"><span data-stu-id="693d5-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="693d5-135">Obecně byste navrhnout svoje knihovny takovým způsobem, že je uložené informace, které jsou pravděpodobně pravidelně měnit v `app.config` souboru tímto způsobem, když dojde k aktualizaci těchto informací právě potřebuje vyměnit s novým konfiguračního souboru starší verze bez nutnosti rekompilace knihovny.</span><span class="sxs-lookup"><span data-stu-id="693d5-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="693d5-136">Použití knihovny</span><span class="sxs-lookup"><span data-stu-id="693d5-136">Consuming Libraries</span></span>

<span data-ttu-id="693d5-137">Jako vývojář, který využívá knihovny .NET vytvořených jinými vývojáři vědět pravděpodobně, že nová verze knihovny nemusí být plně kompatibilní s vaším projektem, takže vám často sami s a aktualizujte svůj kód pro práci s těmito změnami.</span><span class="sxs-lookup"><span data-stu-id="693d5-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="693d5-138">Šťastná za vás C# a ekosystému .NET obsahuje funkce a techniky, které umožňuje snadno aktualizovat naší aplikace pro práci s novými verzemi nástroje knihovny, které můžou zavést rozbíjející změny.</span><span class="sxs-lookup"><span data-stu-id="693d5-138">Lucky for you C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="693d5-139">Přesměrování vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="693d5-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="693d5-140">Můžete použít `app.config` souboru k aktualizaci verze knihovny aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="693d5-140">You can use the `app.config` file to update the version of a library your app uses.</span></span> <span data-ttu-id="693d5-141">Přidáním, co se volá [ *přesměrování vazby* ](../framework/configure-apps/redirect-assembly-versions.md) vaše můžete použít na novou verzi knihovny bez nutnosti znovu kompilovat aplikace.</span><span class="sxs-lookup"><span data-stu-id="693d5-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md) your can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="693d5-142">Následující příklad ukazuje, jak by aktualizovat vaše aplikace `app.config` soubor má být použit `1.0.1` oprav verze `ReferencedLibrary` místo `1.0.0` původně byl kompilován s verzí.</span><span class="sxs-lookup"><span data-stu-id="693d5-142">The following example shows how you would update your app's `app.config` file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="693d5-143">Tento postup bude fungovat jenom v případě novou verzi `ReferencedLibrary` binární kompatibilní s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="693d5-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="693d5-144">Zobrazit [Backwards Compatibility](#backwards-compatibility) výše uvedené části hledejte při určování kompatibility se změny.</span><span class="sxs-lookup"><span data-stu-id="693d5-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="693d5-145">new</span><span class="sxs-lookup"><span data-stu-id="693d5-145">new</span></span>

<span data-ttu-id="693d5-146">Můžete použít `new` modifikátor ke skrytí zděděné členy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="693d5-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="693d5-147">Toto je jeden způsob odvozené třídy může reagovat na aktualizací v základních tříd.</span><span class="sxs-lookup"><span data-stu-id="693d5-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="693d5-148">Proveďte v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="693d5-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="693d5-149">**Output**</span><span class="sxs-lookup"><span data-stu-id="693d5-149">**Output**</span></span>

```
A base method
A derived method
```

<span data-ttu-id="693d5-150">V předchozím příkladu můžete zobrazit jak `DerivedClass` skryje `MyMethod` metody, které jsou k dispozici v `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="693d5-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="693d5-151">To znamená, že když základní třídy v nové verzi knihovny přidá člen, který již existuje v odvozené třídě, můžete jednoduše použít `new` modifikátor vaší odvozené třídě člen skrýt člena základní třídy.</span><span class="sxs-lookup"><span data-stu-id="693d5-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="693d5-152">Pokud ne `new` modifikátor určena, odvozené třídy ve výchozím nastavení skryje konfliktní členy v základní třídě, i když se vygeneruje upozornění kompilátoru kód se stále zkompiluje.</span><span class="sxs-lookup"><span data-stu-id="693d5-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="693d5-153">To znamená, že jednoduše přidání nových členů do existující třídy díky tuto novou verzi knihovny zdroje a binární soubor kompatibilní s kódem, který na něm závisí.</span><span class="sxs-lookup"><span data-stu-id="693d5-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="693d5-154">override</span><span class="sxs-lookup"><span data-stu-id="693d5-154">override</span></span>

<span data-ttu-id="693d5-155">`override` Modifikátor znamená, že odvozené implementace rozšiřuje implementaci člena základní třídy místo skrývá ho.</span><span class="sxs-lookup"><span data-stu-id="693d5-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="693d5-156">Členu základní třídy musí mít `virtual` použit modifikátor.</span><span class="sxs-lookup"><span data-stu-id="693d5-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="693d5-157">**Output**</span><span class="sxs-lookup"><span data-stu-id="693d5-157">**Output**</span></span>

```
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="693d5-158">`override` Modifikátor je vyhodnocen v době kompilace a kompilátor vyvolá chybu, pokud se nenajde virtuální člen přepsat.</span><span class="sxs-lookup"><span data-stu-id="693d5-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="693d5-159">Svoje znalosti v oblasti popsané technik, jakož i pochopíte jaké situacích k jejich použití bude urazily dlouhou cestu a zvýšit tak snadné přechod mezi verzemi knihovny.</span><span class="sxs-lookup"><span data-stu-id="693d5-159">Your knowledge of the discussed techniques as well as your understanding of what situations to use them will go a long way to boost the ease of transition between versions of a library.</span></span>

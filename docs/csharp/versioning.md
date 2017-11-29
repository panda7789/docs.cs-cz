---
title: "C# Správa verzí – Průvodce v C#"
description: "Pochopit, jak funguje správa verzí v C# a rozhraní .NET"
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.date: 01/08/2017
ms.topic: article
ms.prod: visual-studio-dev-14
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 0b671333019c00abafcfb72533e30936f8fc6ad7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="versioning-in-c"></a><span data-ttu-id="de55d-104">Správa verzí v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="de55d-104">Versioning in C#</span></span> #

<span data-ttu-id="de55d-105">V tomto kurzu se dozvíte, jaké verze znamená v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="de55d-105">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="de55d-106">Taky poznáte faktory vzít v úvahu při Správa verzí knihovnu, jakož i upgrade na novou verzi knihovnu.</span><span class="sxs-lookup"><span data-stu-id="de55d-106">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of the a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="de55d-107">Vytváření knihovny</span><span class="sxs-lookup"><span data-stu-id="de55d-107">Authoring Libraries</span></span>

<span data-ttu-id="de55d-108">Jako vývojář, který vytvořil knihovny .NET pro veřejné použijte, když jste většinu pravděpodobně byla v situacích, kdy máte zavádět nové aktualizace.</span><span class="sxs-lookup"><span data-stu-id="de55d-108">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="de55d-109">Jak přejdete o tomto procesu otázkách mnoho, je potřeba zajistit, že je snadný přechod z existujícího kódu na novou verzi své knihovny.</span><span class="sxs-lookup"><span data-stu-id="de55d-109">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="de55d-110">Tady je několik zvážit při vytváření nové verze:</span><span class="sxs-lookup"><span data-stu-id="de55d-110">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="de55d-111">Sémantické verze</span><span class="sxs-lookup"><span data-stu-id="de55d-111">Semantic Versioning</span></span>

<span data-ttu-id="de55d-112">[Sémantické verze](http://semver.org/) (SemVer pro zkrácení) je použita pro verze knihovny a označují konkrétní verze události zásady vytváření názvů.</span><span class="sxs-lookup"><span data-stu-id="de55d-112">[Semantic versioning](http://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="de55d-113">V ideálním případě informace o verzi, poskytnete své knihovny by měly pomoci vývojářům určete kompatibilitu s jejich projektů, které používá starší verzí této stejné knihovny.</span><span class="sxs-lookup"><span data-stu-id="de55d-113">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="de55d-114">Nejzákladnější přístup k SemVer je formát 3 součást `MAJOR.MINOR.PATCH`, kde:</span><span class="sxs-lookup"><span data-stu-id="de55d-114">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>
 
* <span data-ttu-id="de55d-115">`MAJOR`se zvýší, když provedete změny nekompatibilní rozhraní API</span><span class="sxs-lookup"><span data-stu-id="de55d-115">`MAJOR` is incremented when you make incompatible API changes</span></span>
* <span data-ttu-id="de55d-116">`MINOR`se zvýší, když přidáte funkci způsobem zpětně kompatibilní</span><span class="sxs-lookup"><span data-stu-id="de55d-116">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
* <span data-ttu-id="de55d-117">`PATCH`se zvýší, když provedete zpětně kompatibilní opravy chyb</span><span class="sxs-lookup"><span data-stu-id="de55d-117">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="de55d-118">Existují také způsobů určení scénáře jako předprodejní verze atd. při použití informací o verzi do knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="de55d-118">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="de55d-119">Zpětné kompatibility</span><span class="sxs-lookup"><span data-stu-id="de55d-119">Backwards Compatibility</span></span>

<span data-ttu-id="de55d-120">Jak můžete vydání nové verze knihovny, zpětné kompatibility s předchozími verzemi bude pravděpodobně jednou z hlavních věcí.</span><span class="sxs-lookup"><span data-stu-id="de55d-120">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="de55d-121">Nová verze knihovny je zdrojem kompatibilní s předchozí verze, pokud kód, který závisí na předchozí verzi můžete, pokud překompilovat, pracovat s novou verzí.</span><span class="sxs-lookup"><span data-stu-id="de55d-121">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="de55d-122">Pokud aplikace, která závisí na předchozí verzi můžete, bez rekompilace pracovat s novou verzí, je nová verze knihovny binární kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="de55d-122">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="de55d-123">Zde jsou některé věci, které je třeba zvážit při zachování zpětné kompatibility s starší verze knihovny:</span><span class="sxs-lookup"><span data-stu-id="de55d-123">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

* <span data-ttu-id="de55d-124">Virtuální metody: Pokud vytvoříte virtuální metoda nevirtuálních v nové verzi znamená, že bude muset aktualizovat projekty, které potlačí tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="de55d-124">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="de55d-125">Toto je velký narušující změně a se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="de55d-125">This is a huge breaking change and is strongly discouraged.</span></span>
* <span data-ttu-id="de55d-126">Metoda podpisů: při aktualizaci chování metoda vyžaduje, abyste změnit také jeho podpis, měli byste místo toho vytvořit přetížení tak, aby kód volání do dané metody budou i nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="de55d-126">Method signatures: When updating a method behaviour requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="de55d-127">Vždy můžete upravit původní podpis metody provést volání do nové podpis metody tak, aby implementace konzistentní.</span><span class="sxs-lookup"><span data-stu-id="de55d-127">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
* <span data-ttu-id="de55d-128">[Zastaralé atribut](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Tento atribut v kódu můžete použít k určení třídy nebo členy třídy, které jsou zastaralé a mohou být odebrány v budoucích verzích.</span><span class="sxs-lookup"><span data-stu-id="de55d-128">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span>
<span data-ttu-id="de55d-129">Tím se zajistí, že vývojáři využitím knihovnu lépe připravené pro nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="de55d-129">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
* <span data-ttu-id="de55d-130">Nepovinné argumenty metoda: Když provedete metoda dříve volitelné argumenty povinné nebo změnit jejich výchozí hodnoty a všechen kód, který neposkytuje těchto argumentů bude potřeba aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="de55d-130">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>
> [!NOTE]
> <span data-ttu-id="de55d-131">Provedení povinné argumenty nepovinné by měl mít velmi malý vliv, zejména v případě, že se nezmění, metoda chování.</span><span class="sxs-lookup"><span data-stu-id="de55d-131">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behaviour.</span></span>

<span data-ttu-id="de55d-132">Tím snadnější provedete ji pro uživatele k upgradu na novou verzi knihovny, je pravděpodobnější, že se provede upgrade dřív.</span><span class="sxs-lookup"><span data-stu-id="de55d-132">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="de55d-133">Konfigurační soubor aplikace</span><span class="sxs-lookup"><span data-stu-id="de55d-133">Application Configuration File</span></span>

<span data-ttu-id="de55d-134">Jako vývojář .NET existuje velmi vysoká pravděpodobnost byla zjištěna [ `app.config` souboru](https://msdn.microsoft.com/en-us/library/1fk1t1t0(v=vs.110).aspx) ve většině typy projektů.</span><span class="sxs-lookup"><span data-stu-id="de55d-134">As a .NET developer there's a very high chance you've encountered [the `app.config` file](https://msdn.microsoft.com/en-us/library/1fk1t1t0(v=vs.110).aspx) present in most project types.</span></span>
<span data-ttu-id="de55d-135">Tento jednoduchý konfigurační soubor můžete vyhledat celou do zlepšení zavedení nových aktualizací.</span><span class="sxs-lookup"><span data-stu-id="de55d-135">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="de55d-136">Měli byste obecně navrhnout knihovnách tak, že jsou informace, které pravděpodobně se změní pravidelně uložena v `app.config` souboru, tak při aktualizaci tyto informace do konfiguračního souboru starší verze právě je nutné vyměnit novým bez nutnosti rekompilace knihovny.</span><span class="sxs-lookup"><span data-stu-id="de55d-136">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="de55d-137">Použití knihovny</span><span class="sxs-lookup"><span data-stu-id="de55d-137">Consuming Libraries</span></span>

<span data-ttu-id="de55d-138">Jako vývojář, který využívá knihovny .NET vytvořené jinými vývojáři jste s největší pravděpodobností vědět, že novou verzi knihovny nemusí být plně kompatibilní s projektem a může najít často sami nutnosti aktualizujte kód a pracovat s těmito změnami.</span><span class="sxs-lookup"><span data-stu-id="de55d-138">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="de55d-139">Šťastná pro vás C# a ekosystému .NET obsahuje funkce a techniky, které umožňují snadno aktualizovat vaší aplikace pro práci s novými verzemi nástroje knihovny, které může způsobit dodatečné změny.</span><span class="sxs-lookup"><span data-stu-id="de55d-139">Lucky for you C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="de55d-140">Sestavení – přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="de55d-140">Assembly Binding Redirection</span></span>

<span data-ttu-id="de55d-141">Můžete použít `app.config` soubor aktualizovat verzi knihovny vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="de55d-141">You can use the `app.config` file to update the version of a library your app uses.</span></span> <span data-ttu-id="de55d-142">Přidáním, co se nazývá [ *přesměrování vazby* ](https://msdn.microsoft.com/en-us/library/7wd6ex19(v=vs.110).aspx) vaše můžete použít na novou verzi knihovny bez nutnosti její kompilace aplikace.</span><span class="sxs-lookup"><span data-stu-id="de55d-142">By adding what is called a [*binding redirect*](https://msdn.microsoft.com/en-us/library/7wd6ex19(v=vs.110).aspx) your can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="de55d-143">Následující příklad ukazuje, jak by aktualizovat vaše aplikace `app.config` soubor se má použít `1.0.1` oprav verze `ReferencedLibrary` místo `1.0.0` verze byla původně kompilovat s.</span><span class="sxs-lookup"><span data-stu-id="de55d-143">The following example shows how you would update your app's `app.config` file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="de55d-144">Tento postup bude fungovat pouze v případě novou verzi `ReferencedLibrary` je binární kompatibilní s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="de55d-144">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="de55d-145">Najdete v článku [zpětné kompatibility](#backwards-compatibility) část výše změny hledání při určování kompatibility.</span><span class="sxs-lookup"><span data-stu-id="de55d-145">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="de55d-146">new</span><span class="sxs-lookup"><span data-stu-id="de55d-146">new</span></span>

<span data-ttu-id="de55d-147">Můžete použít `new` modifikátor skrytí zděděné členy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="de55d-147">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="de55d-148">To je jedním způsobem odvozené třídy mohou reagovat na aktualizace v základní třídy.</span><span class="sxs-lookup"><span data-stu-id="de55d-148">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="de55d-149">Proveďte v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="de55d-149">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="de55d-150">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="de55d-150">**Output**</span></span>

```
A base method
A derived method
```

<span data-ttu-id="de55d-151">Z výše uvedeném příkladu uvidíte jak `DerivedClass` skryje `MyMethod` metoda součástí `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="de55d-151">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="de55d-152">To znamená, že pokud základní třídu v nové verzi knihovny přidá člena, který již existuje v odvozené třídě, můžete jednoduše použít `new` modifikátor na vaše člen odvozené třídy ke skrytí člen základní třídy.</span><span class="sxs-lookup"><span data-stu-id="de55d-152">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="de55d-153">Pokud ne `new` Modifikátor je zadán, bude ve výchozím nastavení do odvozené třídy skrýt konfliktní členy v základní třídě, i když se vygeneruje upozornění kompilátoru stále kompilací kódu.</span><span class="sxs-lookup"><span data-stu-id="de55d-153">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="de55d-154">To znamená, že jednoduše přidáním nové členy do existující třídy díky nové verze nástroje knihovnu zdrojový i binární kompatibilní s kódem, který na něm závisí.</span><span class="sxs-lookup"><span data-stu-id="de55d-154">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="de55d-155">override</span><span class="sxs-lookup"><span data-stu-id="de55d-155">override</span></span>

<span data-ttu-id="de55d-156">`override` Modifikátor znamená odvozené implementace rozšiřuje implementace člena základní třídy místo skryje ho.</span><span class="sxs-lookup"><span data-stu-id="de55d-156">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="de55d-157">Základní třída člen musí mít `virtual` modifikátor použije na ni.</span><span class="sxs-lookup"><span data-stu-id="de55d-157">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="de55d-158">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="de55d-158">**Output**</span></span>

```
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="de55d-159">`override` Modifikátor je vyhodnocován v době kompilace a kompilátor vyvolá chybu, pokud se nenajde člena virtuální přepsat.</span><span class="sxs-lookup"><span data-stu-id="de55d-159">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="de55d-160">Vašich znalostí technik popsaných i pochopení jaké situacích používat přejde dlouho způsob, jak zvýšit snadný přechod mezi verzemi knihovny.</span><span class="sxs-lookup"><span data-stu-id="de55d-160">Your knowledge of the discussed techniques as well as your understanding of what situations to use them will go a long way to boost the ease of transition between versions of a library.</span></span>

---
title: C# Správa verzí – průvodce C#
description: Zjistěte, jak funguje správa verzí v c# a .NET
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 124cce51865f04a555bc121fb6ce18cc95591bdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156464"
---
# <a name="versioning-in-c"></a><span data-ttu-id="a4a3d-103">Správa verzí v C\#</span><span class="sxs-lookup"><span data-stu-id="a4a3d-103">Versioning in C\#</span></span>

<span data-ttu-id="a4a3d-104">V tomto kurzu se dozvíte, co znamená správa verzí v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="a4a3d-105">Dozvíte se také faktory, které je třeba vzít v úvahu při snímání verzí knihovny a upgradu na novou verzi knihovny.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="a4a3d-106">Vytváření knihoven</span><span class="sxs-lookup"><span data-stu-id="a4a3d-106">Authoring Libraries</span></span>

<span data-ttu-id="a4a3d-107">Jako vývojář, který vytvořil knihovny .NET pro veřejné použití, jste s největší pravděpodobností byli v situacích, kdy budete muset zavést nové aktualizace.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="a4a3d-108">Jak jít o tomto procesu záleží hodně, jak je třeba zajistit, že je bezproblémový přechod existujícího kódu na novou verzi knihovny.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="a4a3d-109">Zde je několik věcí, které je třeba zvážit při vytváření nové verze:</span><span class="sxs-lookup"><span data-stu-id="a4a3d-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="a4a3d-110">Sémantická správa verzí</span><span class="sxs-lookup"><span data-stu-id="a4a3d-110">Semantic Versioning</span></span>

<span data-ttu-id="a4a3d-111">[Sémantická správa verzí](https://semver.org/) (zkráceně SemVer) je konvence pojmenování použitá pro verze knihovny, která označuje konkrétní události milníků.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-111">[Semantic versioning](https://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="a4a3d-112">V ideálním případě by informace o verzi, které poskytujete knihovně, měly vývojářům pomoci určit kompatibilitu s jejich projekty, které využívají starší verze stejné knihovny.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="a4a3d-113">Nejzákladnější přístup k SemVer je `MAJOR.MINOR.PATCH`3 složka formátu , kde:</span><span class="sxs-lookup"><span data-stu-id="a4a3d-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

- <span data-ttu-id="a4a3d-114">`MAJOR`je se zpřísněn, když provedete nekompatibilní změny rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a4a3d-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
- <span data-ttu-id="a4a3d-115">`MINOR`je se zvýší, když přidáte funkce zpětně kompatibilním způsobem</span><span class="sxs-lookup"><span data-stu-id="a4a3d-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
- <span data-ttu-id="a4a3d-116">`PATCH`je se zpřísněn, když provedete opravy chyb kompatibilní se zpětnou kompatibilitou</span><span class="sxs-lookup"><span data-stu-id="a4a3d-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="a4a3d-117">Existují také způsoby, jak zadat další scénáře, jako jsou předběžné verze atd.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="a4a3d-118">Zpětná kompatibilita</span><span class="sxs-lookup"><span data-stu-id="a4a3d-118">Backwards Compatibility</span></span>

<span data-ttu-id="a4a3d-119">Při vydávání nových verzí knihovny bude zpětná kompatibilita s předchozími verzemi s největší pravděpodobností jednou z vašich hlavních obav.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="a4a3d-120">Nová verze knihovny je zdroj kompatibilní s předchozí verzí, pokud kód, který závisí na předchozí verzi může při překompilování pracovat s novou verzí.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span>
<span data-ttu-id="a4a3d-121">Nová verze knihovny je binární kompatibilní, pokud aplikace, která závisela na staré verzi, může bez rekompilace pracovat s novou verzí.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="a4a3d-122">Při pokusu o zachování zpětné kompatibility se staršími verzemi knihovny je třeba zvážit několik věcí:</span><span class="sxs-lookup"><span data-stu-id="a4a3d-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

- <span data-ttu-id="a4a3d-123">Virtuální metody: Pokud vytvoříte virtuální metodu nevirtuální v nové verzi, znamená to, že projekty, které tuto metodu přepíší, budou muset být aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="a4a3d-124">Jedná se o obrovskou průlomovou změnu a je silně odrazována.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-124">This is a huge breaking change and is strongly discouraged.</span></span>
- <span data-ttu-id="a4a3d-125">Podpisy metody: Při aktualizaci chování metody vyžaduje také změnit jeho podpis, měli byste místo toho vytvořit přetížení tak, aby kód volající do této metody bude i nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-125">Method signatures: When updating a method behavior requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="a4a3d-126">Vždy můžete manipulovat starý podpis metody volat do podpisu nové metody tak, aby implementace zůstává konzistentní.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
- <span data-ttu-id="a4a3d-127">[Zastaralý atribut](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Tento atribut v kódu můžete použít k určení tříd nebo členů tříd, které jsou zastaralé a pravděpodobně budou odebrány v budoucích verzích.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-127">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span> <span data-ttu-id="a4a3d-128">Tím je zajištěno, že vývojáři využívající vaši knihovnu jsou lépe připraveni na nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
- <span data-ttu-id="a4a3d-129">Volitelné argumenty metody: Pokud provedete dříve volitelné argumenty metody povinné nebo změnit jejich výchozí hodnotu pak veškerý kód, který neposkytuje tyto argumenty bude muset být aktualizován.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>

> [!NOTE]
> <span data-ttu-id="a4a3d-130">Povinné argumenty by měly mít velmi malý účinek, zejména pokud nezmění chování metody.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behavior.</span></span>

<span data-ttu-id="a4a3d-131">Čím snadněji provedete upgrade na novou verzi knihovny uživatelům, tím je pravděpodobnější, že budou upgradovat dříve.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="a4a3d-132">Konfigurační soubor aplikace</span><span class="sxs-lookup"><span data-stu-id="a4a3d-132">Application Configuration File</span></span>

<span data-ttu-id="a4a3d-133">Jako vývojář rozhraní .NET je velmi vysoká pravděpodobnost, že jste narazili [na `app.config` soubor](../framework/configure-apps/file-schema/index.md) přítomný ve většině typů projektů.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="a4a3d-134">Tento jednoduchý konfigurační soubor může jít dlouhou cestu do zlepšení zavádění nových aktualizací.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="a4a3d-135">Obecně byste měli navrhnout knihovny tak, aby informace, které se `app.config` pravděpodobně pravidelně mění, byly uloženy v souboru, a tak při aktualizaci těchto informací musí být konfigurační soubor starších verzí nahrazen novým bez nutnosti rekompilace knihovny.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated, the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="a4a3d-136">Náročné knihovny</span><span class="sxs-lookup"><span data-stu-id="a4a3d-136">Consuming Libraries</span></span>

<span data-ttu-id="a4a3d-137">Jako vývojář, který využívá knihovny .NET vytvořené jinými vývojáři, jste si s největší pravděpodobností vědomi toho, že nová verze knihovny nemusí být plně kompatibilní s vaším projektem a často se často ocitnete museli aktualizovat kód pro práci s těmito změnami.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="a4a3d-138">Naštěstí pro vás, C# a .NET ekosystém přichází s funkcemi a technikami, které nám umožňují snadno aktualizovat naši aplikaci pro práci s novými verzemi knihoven, které by mohly zavést nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-138">Lucky for you, C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="a4a3d-139">Přesměrování vazeb sestavy</span><span class="sxs-lookup"><span data-stu-id="a4a3d-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="a4a3d-140">Pomocí souboru *app.config* můžete aktualizovat verzi knihovny, kterou vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-140">You can use the *app.config* file to update the version of a library your app uses.</span></span> <span data-ttu-id="a4a3d-141">Přidáním takzvaného [*přesměrování vazby*](../framework/configure-apps/redirect-assembly-versions.md)můžete použít novou verzi knihovny, aniž byste museli znovu kompilovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md), you can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="a4a3d-142">Následující příklad ukazuje, jak byste aktualizovali soubor *app.config* aplikace `ReferencedLibrary` tak, `1.0.0` aby používal verzi `1.0.1` opravy namísto verze, ve které byl původně zkompilován.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-142">The following example shows how you would update your app's *app.config* file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="a4a3d-143">Tento přístup bude fungovat pouze `ReferencedLibrary` v případě, že nová verze je binární kompatibilní s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="a4a3d-144">Změny, na které je třeba dávat pozor při určování kompatibility, najdete v části [Zpětná kompatibilita](#backwards-compatibility) výše.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="a4a3d-145">new</span><span class="sxs-lookup"><span data-stu-id="a4a3d-145">new</span></span>

<span data-ttu-id="a4a3d-146">`new` Modifikátor slouží ke skrytí zděděných členů základní třídy.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="a4a3d-147">Toto je jeden způsob, jak odvozené třídy mohou reagovat na aktualizace v základních třídách.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="a4a3d-148">Vezměte v následující příklad:</span><span class="sxs-lookup"><span data-stu-id="a4a3d-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="a4a3d-149">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="a4a3d-149">**Output**</span></span>

```console
A base method
A derived method
```

<span data-ttu-id="a4a3d-150">Z výše uvedeného příkladu můžete vidět, jak `DerivedClass` skryje metodu přítomnou `MyMethod` v `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="a4a3d-151">To znamená, že když základní třída v nové verzi knihovny přidá člen, který již existuje `new` v odvozené třídě, můžete jednoduše použít modifikátor na člen odvozené třídy skrýt člen základní třídy.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="a4a3d-152">Pokud `new` není zadán žádný modifikátor, odvozená třída bude ve výchozím nastavení skrývat konfliktní členy v základní třídě, i když bude generováno upozornění kompilátoru, kód bude stále kompilován.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="a4a3d-153">To znamená, že jednoduše přidání nových členů do existující třídy způsobí, že nová verze knihovny zdrojové i binární kompatibilní s kódem, který na něm závisí.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="a4a3d-154">override</span><span class="sxs-lookup"><span data-stu-id="a4a3d-154">override</span></span>

<span data-ttu-id="a4a3d-155">Modifikátor `override` znamená, že odvozená implementace rozšiřuje implementaci člena základní třídy, nikoli jej skryje.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="a4a3d-156">Člen základní třídy musí `virtual` mít modifikátor použít.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="a4a3d-157">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="a4a3d-157">**Output**</span></span>

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="a4a3d-158">Modifikátor `override` je vyhodnocen v době kompilace a kompilátor vyvolá chybu, pokud nenajde virtuálního člena přepsat.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="a4a3d-159">Vaše znalosti diskutovaných technik a vaše chápání situací, ve kterých je používat, půjdou dlouhou cestu k usnadnění přechodu mezi verzemi knihovny.</span><span class="sxs-lookup"><span data-stu-id="a4a3d-159">Your knowledge of the discussed techniques and your understanding of the situations in which to use them, will go a long way towards easing the transition between versions of a library.</span></span>

---
title: C#C# Průvodce správou verzí
description: Informace o tom, jak funguje C# Správa verzí v prostředí a .NET
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: bfad7abe6b2b5c6a19324656963a79212a317110
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926584"
---
# <a name="versioning-in-c"></a><span data-ttu-id="eba95-103">Správa verzí v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="eba95-103">Versioning in C\#</span></span>

<span data-ttu-id="eba95-104">V tomto kurzu se dozvíte, co znamená Správa verzí v .NET.</span><span class="sxs-lookup"><span data-stu-id="eba95-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="eba95-105">Dozvíte se také o faktorech, které je potřeba vzít v úvahu při použití verze knihovny a upgradu na novou verzi knihovny.</span><span class="sxs-lookup"><span data-stu-id="eba95-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="eba95-106">Vytváření knihoven</span><span class="sxs-lookup"><span data-stu-id="eba95-106">Authoring Libraries</span></span>

<span data-ttu-id="eba95-107">Jako vývojář, který vytvořil knihovny .NET pro veřejné použití, jste pravděpodobně v situacích, kdy je nutné zavést nové aktualizace.</span><span class="sxs-lookup"><span data-stu-id="eba95-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="eba95-108">Způsob, jakým se dozvíte o tomto procesu, záleží na tom, co potřebujete, abyste zajistili bezproblémové přechody stávajícího kódu na novou verzi vaší knihovny.</span><span class="sxs-lookup"><span data-stu-id="eba95-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="eba95-109">Při vytváření nové verze je potřeba vzít v úvahu několik věcí:</span><span class="sxs-lookup"><span data-stu-id="eba95-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="eba95-110">Sémantická verze</span><span class="sxs-lookup"><span data-stu-id="eba95-110">Semantic Versioning</span></span>

<span data-ttu-id="eba95-111">[Sémantická verze](https://semver.org/) (SemVer pro krátké) je konvence pojmenování, která se používá ve verzích vaší knihovny k označení konkrétních událostí milníku.</span><span class="sxs-lookup"><span data-stu-id="eba95-111">[Semantic versioning](https://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="eba95-112">V ideálním případě informace o verzi vaší knihovny by vám měly pomáhat vývojářům určit kompatibilitu s jejich projekty, které využívají starší verze stejné knihovny.</span><span class="sxs-lookup"><span data-stu-id="eba95-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="eba95-113">Nejzákladnější přístup k SemVer je 3 formát `MAJOR.MINOR.PATCH`komponenty, kde:</span><span class="sxs-lookup"><span data-stu-id="eba95-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

* <span data-ttu-id="eba95-114">`MAJOR`se zvýší, když provedete nekompatibilní změny rozhraní API</span><span class="sxs-lookup"><span data-stu-id="eba95-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
* <span data-ttu-id="eba95-115">`MINOR`se zvýší, když přidáváte funkce zpětně kompatibilním způsobem.</span><span class="sxs-lookup"><span data-stu-id="eba95-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
* <span data-ttu-id="eba95-116">`PATCH`se zvýší, když provedete zpětně kompatibilní opravy chyb.</span><span class="sxs-lookup"><span data-stu-id="eba95-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="eba95-117">Existují také způsoby určení dalších scénářů, jako jsou předběžné verze verzí atd. při použití informací o verzi do knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="eba95-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="eba95-118">Zpětná kompatibilita</span><span class="sxs-lookup"><span data-stu-id="eba95-118">Backwards Compatibility</span></span>

<span data-ttu-id="eba95-119">Při vydávání nových verzí knihovny bude zpětná kompatibilita s předchozími verzemi pravděpodobně jedním z vašich hlavních otázek.</span><span class="sxs-lookup"><span data-stu-id="eba95-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="eba95-120">Nová verze knihovny je kompatibilní se zdrojem předchozí verze, pokud kód, který závisí na předchozí verzi, může při rekompilaci fungovat s novou verzí.</span><span class="sxs-lookup"><span data-stu-id="eba95-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="eba95-121">Nová verze knihovny je binární, kompatibilní, pokud aplikace, která závisí na staré verzi, může bez rekompilace fungovat s novou verzí.</span><span class="sxs-lookup"><span data-stu-id="eba95-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="eba95-122">Tady je několik věcí, které je potřeba vzít v úvahu při pokusu o udržení zpětné kompatibility se staršími verzemi vaší knihovny:</span><span class="sxs-lookup"><span data-stu-id="eba95-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

* <span data-ttu-id="eba95-123">Virtuální metody: Když vytvoříte virtuální metodu v nové verzi jako nevirtuální, znamená to, že by se měly aktualizovat projekty, které tuto metodu přepisují.</span><span class="sxs-lookup"><span data-stu-id="eba95-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="eba95-124">Jedná se o velmi zásadní změnu a důrazně se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="eba95-124">This is a huge breaking change and is strongly discouraged.</span></span>
* <span data-ttu-id="eba95-125">Signatury metody: V případě, že se při aktualizaci chování metody vyžaduje, abyste změnili jeho signaturu, měli byste místo toho vytvořit přetížení, aby kód, který volá tuto metodu, bude stále fungovat.</span><span class="sxs-lookup"><span data-stu-id="eba95-125">Method signatures: When updating a method behaviour requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="eba95-126">Můžete vždycky manipulovat s podpisem staré metody, aby se volal do nového podpisu metody, takže implementace zůstane konzistentní.</span><span class="sxs-lookup"><span data-stu-id="eba95-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
* <span data-ttu-id="eba95-127">[Zastaralý atribut](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Pomocí tohoto atributu v kódu můžete určit třídy nebo členy třídy, které jsou zastaralé a pravděpodobně budou odebrány v budoucích verzích.</span><span class="sxs-lookup"><span data-stu-id="eba95-127">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span> <span data-ttu-id="eba95-128">Tím je zajištěno, že vývojáři, kteří využívají vaši knihovnu, budou lépe připraveni na zásadní změny.</span><span class="sxs-lookup"><span data-stu-id="eba95-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
* <span data-ttu-id="eba95-129">Volitelné argumenty metody: Pokud ponecháte dříve volitelné argumenty metody jako povinné nebo změníte jejich výchozí hodnotu, bude nutné aktualizovat veškerý kód, který tyto argumenty nedodá.</span><span class="sxs-lookup"><span data-stu-id="eba95-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>

> [!NOTE]
> <span data-ttu-id="eba95-130">Volitelná povinná argumenty by měly mít velmi malý účinek, zejména pokud nemění chování metody.</span><span class="sxs-lookup"><span data-stu-id="eba95-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behaviour.</span></span>

<span data-ttu-id="eba95-131">To je snazší, když uživatelům umožníte upgradovat na novou verzi knihovny, což je pravděpodobnější, že budou upgradovat dřív.</span><span class="sxs-lookup"><span data-stu-id="eba95-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="eba95-132">Konfigurační soubor aplikace</span><span class="sxs-lookup"><span data-stu-id="eba95-132">Application Configuration File</span></span>

<span data-ttu-id="eba95-133">Jako vývojář rozhraní .NET existuje velmi vysoká pravděpodobnost, že [se `app.config` soubor](../framework/configure-apps/file-schema/index.md) nachází ve většině typů projektů.</span><span class="sxs-lookup"><span data-stu-id="eba95-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="eba95-134">Tento jednoduchý konfigurační soubor může být delší způsob, jak zlepšit zavedení nových aktualizací.</span><span class="sxs-lookup"><span data-stu-id="eba95-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="eba95-135">Obecně byste měli navrhovat knihovny tak, aby se informace, které se pravděpodobně mění pravidelně, ukládaly do `app.config` souboru, a to tak, že se tyto informace aktualizují. konfigurační soubor starších verzí stačí nahradit novým bez nutnosti rekompilace knihovny.</span><span class="sxs-lookup"><span data-stu-id="eba95-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="eba95-136">Využívání knihoven</span><span class="sxs-lookup"><span data-stu-id="eba95-136">Consuming Libraries</span></span>

<span data-ttu-id="eba95-137">Jako vývojář, který využívá knihovny .NET vytvořené jinými vývojáři, s největší pravděpodobně víte, že nová verze knihovny nemusí být plně kompatibilní s vaším projektem, a je možné, že často budete muset aktualizovat kód pro práci s těmito změnami.</span><span class="sxs-lookup"><span data-stu-id="eba95-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="eba95-138">Štěstí pro vás C# a ekosystém .NET přináší funkce a techniky, které nám umožňují snadno aktualizovat naši aplikaci, aby fungovala s novými verzemi knihoven, které můžou zavádět zásadní změny.</span><span class="sxs-lookup"><span data-stu-id="eba95-138">Lucky for you C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="eba95-139">Přesměrování vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="eba95-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="eba95-140">`app.config` Soubor můžete použít k aktualizaci verze knihovny, kterou vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="eba95-140">You can use the `app.config` file to update the version of a library your app uses.</span></span> <span data-ttu-id="eba95-141">Přidáním toho, co se nazývá [*přesměrování vazby*](../framework/configure-apps/redirect-assembly-versions.md) , můžete použít novou verzi knihovny, aniž byste museli aplikaci znovu kompilovat.</span><span class="sxs-lookup"><span data-stu-id="eba95-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md) you can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="eba95-142">Následující příklad ukazuje `app.config` , jak byste aktualizovali soubor aplikace tak, aby `1.0.1` používal opravu `1.0.0` verze `ReferencedLibrary` místo verze, ve které byla původně zkompilována.</span><span class="sxs-lookup"><span data-stu-id="eba95-142">The following example shows how you would update your app's `app.config` file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="eba95-143">Tento přístup bude fungovat jenom v případě, že `ReferencedLibrary` je nová verze binárního souboru kompatibilního s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="eba95-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="eba95-144">V části [Zpětná kompatibilita](#backwards-compatibility) výše najdete změny, které je potřeba zobrazit při určování kompatibility.</span><span class="sxs-lookup"><span data-stu-id="eba95-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="eba95-145">new</span><span class="sxs-lookup"><span data-stu-id="eba95-145">new</span></span>

<span data-ttu-id="eba95-146">Použijete `new` modifikátor ke skrytí zděděných členů základní třídy.</span><span class="sxs-lookup"><span data-stu-id="eba95-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="eba95-147">Toto je jeden ze způsobů, které odvozené třídy mohou reagovat na aktualizace v základních třídách.</span><span class="sxs-lookup"><span data-stu-id="eba95-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="eba95-148">Vezměte v úvahu následující příklad:</span><span class="sxs-lookup"><span data-stu-id="eba95-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="eba95-149">**Output**</span><span class="sxs-lookup"><span data-stu-id="eba95-149">**Output**</span></span>

```
A base method
A derived method
```

<span data-ttu-id="eba95-150">Z výše uvedeného příkladu vidíte, jak `DerivedClass` skrývá metodu, která je `MyMethod` k `BaseClass`dispozici v.</span><span class="sxs-lookup"><span data-stu-id="eba95-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="eba95-151">To znamená, že když základní třída v nové verzi knihovny přidá člena, který již existuje v odvozené třídě, můžete jednoduše použít `new` modifikátor na odvozeném členu třídy pro skrytí člena základní třídy.</span><span class="sxs-lookup"><span data-stu-id="eba95-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="eba95-152">Pokud není `new` zadán žádný modifikátor, bude ve výchozím nastavení v odvozené třídě standardně skryty konfliktní členy základní třídy, i když bude vygenerováno upozornění kompilátoru, kód bude stále zkompilován.</span><span class="sxs-lookup"><span data-stu-id="eba95-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="eba95-153">To znamená, že pouhým přidáním nových členů do existující třídy dojde k tomu, že nová verze knihovny je kompatibilní se zdrojovým i binárním kódem, který na něm závisí.</span><span class="sxs-lookup"><span data-stu-id="eba95-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="eba95-154">override</span><span class="sxs-lookup"><span data-stu-id="eba95-154">override</span></span>

<span data-ttu-id="eba95-155">`override` Modifikátor znamená, že odvozená implementace rozšiřuje implementaci člena základní třídy místo jeho skrytí.</span><span class="sxs-lookup"><span data-stu-id="eba95-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="eba95-156">Člen základní třídy musí mít `virtual` použit modifikátor.</span><span class="sxs-lookup"><span data-stu-id="eba95-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="eba95-157">**Output**</span><span class="sxs-lookup"><span data-stu-id="eba95-157">**Output**</span></span>

```
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="eba95-158">`override` Modifikátor je vyhodnocen v době kompilace a kompilátor vyvolá chybu, pokud nenajde virtuální člen, který se má přepsat.</span><span class="sxs-lookup"><span data-stu-id="eba95-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="eba95-159">Vaše znalosti o popisovaných technikách a také porozumění situacím, které se mají použít, budou mít dlouhý způsob, jak zvýšit přehlednost mezi verzemi knihovny.</span><span class="sxs-lookup"><span data-stu-id="eba95-159">Your knowledge of the discussed techniques as well as your understanding of what situations to use them will go a long way to boost the ease of transition between versions of a library.</span></span>
 
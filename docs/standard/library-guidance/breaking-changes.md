---
title: Nejnovější změny a knihovny .NET
description: Doporučení osvědčených postupů pro navigaci nejnovější změny při vytváření knihoven .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 2cbd9e0a818b52aede6c9b1f60fdf52dcbd7b96f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400419"
---
# <a name="breaking-changes"></a><span data-ttu-id="eb8ba-103">Změny způsobující chyby</span><span class="sxs-lookup"><span data-stu-id="eb8ba-103">Breaking changes</span></span>

<span data-ttu-id="eb8ba-104">Je důležité, aby knihovna .NET nalezla rovnováhu mezi stabilitou pro stávající uživatele a inovacemi do budoucna.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="eb8ba-105">Autoři knihovny se přiklánějí k refaktoringu a přehodnocení kódu, dokud není dokonalý, ale porušení stávajících uživatelů má negativní dopad, zejména pro knihovny nižší úrovně.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="eb8ba-106">Typy projektů a narušující změny</span><span class="sxs-lookup"><span data-stu-id="eb8ba-106">Project types and breaking changes</span></span>

<span data-ttu-id="eb8ba-107">Způsob použití knihovny komunitou .NET změní vliv narušujících změn na vývojáře koncových uživatelů.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

- <span data-ttu-id="eb8ba-108">**Knihovny nízké a střední úrovně,** jako je serializátor, analyzátor HTML, mapovač databázových objektů a relačních mapovačů nebo webový rámec, jsou nejvíce ovlivněny nejnovějšími změnami.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="eb8ba-109">Balíčky stavebních bloků používají vývojáři koncových uživatelů k vytváření aplikací a další knihovny jako závislosti NuGet.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="eb8ba-110">Například vytváříte aplikaci a používáte klienta s otevřeným zdrojovým kódem k volání webové služby.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="eb8ba-111">Narušující aktualizace závislosti, kterou klient používá, není něco, co můžete opravit.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="eb8ba-112">Je to open-source klient, který je třeba změnit a nemáte nad ním žádnou kontrolu.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="eb8ba-113">Musíte najít kompatibilní verze knihoven nebo odeslat opravu do klientské knihovny a čekat na novou verzi.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="eb8ba-114">Nejhorší situace je, pokud chcete použít dvě knihovny, které závisí na vzájemně nekompatibilní verze třetí knihovny.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

- <span data-ttu-id="eb8ba-115">**Knihovny na vysoké úrovni,** jako je sada ovládacích prvků uživatelského rozhraní, jsou méně citlivé na narušující změny.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="eb8ba-116">Knihovny vysoké úrovně jsou přímo odkazovány v aplikaci koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="eb8ba-117">Pokud dojde k narušující změny, vývojář může zvolit aktualizaci na nejnovější verzi nebo můžete upravit jejich aplikace pro práci s narušující změny.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="eb8ba-118">✔️ přemýšlejte o tom, jak bude vaše knihovna použita.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-118">✔️ DO think about how your library will be used.</span></span> <span data-ttu-id="eb8ba-119">Jaký vliv budou mít změny na aplikace a knihovny, které je používají?</span><span class="sxs-lookup"><span data-stu-id="eb8ba-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="eb8ba-120">✔️ při vývoji nízkoúrovňové knihovny .NET minimalizují narušující změny.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-120">✔️ DO minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="eb8ba-121">✔️ zvážit publikování hlavní přepsání knihovny jako nový balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-121">✔️ CONSIDER publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="eb8ba-122">Typy přerušovatých změn</span><span class="sxs-lookup"><span data-stu-id="eb8ba-122">Types of breaking changes</span></span>

<span data-ttu-id="eb8ba-123">Nejnovější změny spadají do různých kategorií a nemají stejný vliv.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="eb8ba-124">Změna rozdělení zdroje</span><span class="sxs-lookup"><span data-stu-id="eb8ba-124">Source breaking change</span></span>

<span data-ttu-id="eb8ba-125">Změna přerušení zdroje nemá vliv na spuštění programu, ale způsobí chyby kompilace při příštím překompilování aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="eb8ba-126">Například nové přetížení může vytvořit nejednoznačnost v volání metody, které byly jednoznačné dříve nebo přejmenovaný parametr zlomí volající, kteří používají pojmenované parametry.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="eb8ba-127">Vzhledem k tomu, že změna rozdělení zdroje je škodlivá pouze v případě, že vývojáři překompilují své aplikace, je to nejméně rušivá změna.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="eb8ba-128">Vývojáři mohou snadno opravit svůj vlastní poškozený zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="eb8ba-129">Změna narušující chování</span><span class="sxs-lookup"><span data-stu-id="eb8ba-129">Behavior breaking change</span></span>

<span data-ttu-id="eb8ba-130">Změny chování jsou nejčastějším typem narušující změny: téměř každá změna v chování může někoho zlomit.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="eb8ba-131">Změny v knihovně, jako jsou podpisy metod, výjimky vyvržené nebo vstupní nebo výstupní datové formáty, mohou negativně ovlivnit spotřebitele knihovny.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="eb8ba-132">I oprava chyby může být kvalifikována jako narušující změna, pokud se uživatelé spoléhali na dříve přerušené chování.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="eb8ba-133">Přidání funkcí a zlepšení špatnéchování je dobrá věc, ale bez péče to může dělat to velmi těžké pro stávající uživatele k upgradu.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="eb8ba-134">Jedním z přístupů, který vývojářům pomáhá vypořádat se se změnami narušujícím chování, je skrýt je za nastavení.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="eb8ba-135">Nastavení umožňují vývojářům aktualizovat na nejnovější verzi knihovny a zároveň se rozhodnout, že se přihlásí nebo odhlásí z nejnovějších změn.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="eb8ba-136">Tato strategie umožňuje vývojářům zůstat aktuální a zároveň umožňuje jejich náročné kód přizpůsobit v průběhu času.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="eb8ba-137">Například ASP.NET Core MVC má koncept [verze kompatibility,](/aspnet/core/mvc/compatibility-version) která upravuje funkce `MvcOptions`povolené a zakázané na .</span><span class="sxs-lookup"><span data-stu-id="eb8ba-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="eb8ba-138">✔️ ZVAŽTe ponechání nových funkcí ve výchozím nastavení vypnuté, pokud ovlivňují stávající uživatele, a nechte vývojáře, aby se k této funkci přihlásili pomocí nastavení.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-138">✔️ CONSIDER leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="eb8ba-139">Binární změna porušení</span><span class="sxs-lookup"><span data-stu-id="eb8ba-139">Binary breaking change</span></span>

<span data-ttu-id="eb8ba-140">Binární narušující změna se stane, když změníte veřejné rozhraní API knihovny, takže sestavení zkompilovaná proti starší verze knihovny již nejsou moci volat rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="eb8ba-141">Například změna podpisu metody přidáním nového parametru způsobí, že sestavení zkompilovaná <xref:System.MissingMethodException>proti starší verzi knihovny vyvolá .</span><span class="sxs-lookup"><span data-stu-id="eb8ba-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="eb8ba-142">Binární změna rozdělení může také přerušit **celé sestavení**.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="eb8ba-143">Přejmenování sestavení `AssemblyName` pomocí změní identitu sestavení, stejně jako přidání, odebrání nebo změna silného pojmenovávacího klíče sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="eb8ba-144">Změna identity sestavení přeruší veškerý zkompilovaný kód, který jej používá.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="eb8ba-145">❌NEMĚŇTE název sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-145">❌ DO NOT change an assembly name.</span></span>

<span data-ttu-id="eb8ba-146">❌NEPŘIdávejte, neodebírejte ani neměňte silný pojmenovávacím klíčem.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-146">❌ DO NOT add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="eb8ba-147">✔️ zvážit použití abstraktní základní třídy namísto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-147">✔️ CONSIDER using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="eb8ba-148">Přidání cokoli v rozhraní způsobí, že existující typy, které implementují k selhání.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="eb8ba-149">Abstraktní základní třída umožňuje přidat výchozí virtuální implementaci.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="eb8ba-150">✔️ ZVAŽTe <xref:System.ObsoleteAttribute> umístění na typy a členy, které chcete odebrat.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-150">✔️ CONSIDER placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="eb8ba-151">Atribut by měl mít pokyny pro aktualizaci kódu, aby již nepoužíval zastaralé rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="eb8ba-152">Kód, který volá typy <xref:System.ObsoleteAttribute> a metody s bude generovat upozornění sestavení se zprávou zadanou atributu.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="eb8ba-153">Upozornění poskytují lidem, kteří používají zastaralé rozhraní API povrchčas k migraci tak, že při odebrání zastaralé rozhraní API, většina z nich již používat.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

<span data-ttu-id="eb8ba-154">✔️ zvažte zachování typů <xref:System.ObsoleteAttribute> a metod s neomezeně dlouho v knihovnách nízké a střední úrovně.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-154">✔️ CONSIDER keeping types and methods with the <xref:System.ObsoleteAttribute> indefinitely in low and middle-level libraries.</span></span>

> <span data-ttu-id="eb8ba-155">Odebrání api je binární narušující změna.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-155">Removing APIs is a binary breaking change.</span></span> <span data-ttu-id="eb8ba-156">Vzhledem k zachování zastaralých typů a metod, pokud jejich údržba je nízká cena a nepřidává mnoho technických dluhů do vaší knihovny.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-156">Considering keeping obsolete types and methods if maintaining them is low cost and doesn't add lot of technical debt to your library.</span></span> <span data-ttu-id="eb8ba-157">Není odebrání typů a metod může pomoci vyhnout se nejhorší scénáře uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="eb8ba-157">Not removing types and methods can help avoid the worst-case scenarios mentioned above.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb8ba-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb8ba-158">See also</span></span>

- [<span data-ttu-id="eb8ba-159">Důležité informace o verzi a aktualizaci pro vývojáře jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eb8ba-159">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
- [<span data-ttu-id="eb8ba-160">Definitivní průvodce změny rozhraní API-lámání v .NET</span><span class="sxs-lookup"><span data-stu-id="eb8ba-160">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [<span data-ttu-id="eb8ba-161">Pravidla pro porušení pravidel změn rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="eb8ba-161">.NET breaking change rules</span></span>](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="eb8ba-162">Předchozí</span><span class="sxs-lookup"><span data-stu-id="eb8ba-162">Previous</span></span>](versioning.md)

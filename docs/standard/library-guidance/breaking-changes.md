---
title: Zásadní změny a knihoven .NET
description: Doporučení osvědčených postupů pro navigaci rozbíjející změny v při vytváření knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: abea715cd93ae585ef0eef7747f6ace4e5d347ae
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2018
ms.locfileid: "48914199"
---
# <a name="breaking-changes"></a><span data-ttu-id="dfd53-103">Rozbíjející změny v</span><span class="sxs-lookup"><span data-stu-id="dfd53-103">Breaking changes</span></span>

<span data-ttu-id="dfd53-104">Je důležité pro knihovnu .NET najít rovnováhu mezi stabilitu pro stávající uživatele a inovace v budoucnosti.</span><span class="sxs-lookup"><span data-stu-id="dfd53-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="dfd53-105">Další knihovny autoři Refaktoring a jiný pohled kód, dokud je ideálním řešením, ale vaše stávající uživatele dopadem na dřívější kód má negativní dopad, zejména pro knihovny nízké úrovně.</span><span class="sxs-lookup"><span data-stu-id="dfd53-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="dfd53-106">Typy projektů a nejnovější změny</span><span class="sxs-lookup"><span data-stu-id="dfd53-106">Project types and breaking changes</span></span>

<span data-ttu-id="dfd53-107">Použití knihovny .NET komunitou změní účinek rozbíjející změny v vývojáři představující koncové uživatele.</span><span class="sxs-lookup"><span data-stu-id="dfd53-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

* <span data-ttu-id="dfd53-108">**Nízká a střední úrovně knihovny** jako serializátor, analyzátor HTML, objektově relační Mapovač databáze nebo webové rozhraní jsou nejvíce ovlivněné rozbíjející změny.</span><span class="sxs-lookup"><span data-stu-id="dfd53-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="dfd53-109">Balíčky stavebních bloků se používají vývojáři představující koncové uživatele k vytváření aplikací a dalších knihoven jako závislostí NuGet.</span><span class="sxs-lookup"><span data-stu-id="dfd53-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="dfd53-110">Například vytváříte aplikaci a pomocí open source klientské volání webové služby.</span><span class="sxs-lookup"><span data-stu-id="dfd53-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="dfd53-111">Nejnovější aktualizace pro závislost, kterou klient používá není něco, co můžete opravit.</span><span class="sxs-lookup"><span data-stu-id="dfd53-111">A breaking update to dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="dfd53-112">Je open source klientské, kterou je potřeba změnit a nemáte žádnou kontrolu nad ním.</span><span class="sxs-lookup"><span data-stu-id="dfd53-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="dfd53-113">Budete muset najít kompatibilní verze knihoven nebo odeslat oprava klientské knihovny a počkat na novou verzi.</span><span class="sxs-lookup"><span data-stu-id="dfd53-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="dfd53-114">Nejhorším situace je, pokud budete chtít používat dva knihovny, které jsou závislé na vzájemně nekompatibilní verze knihovny třetí.</span><span class="sxs-lookup"><span data-stu-id="dfd53-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

* <span data-ttu-id="dfd53-115">**Základní knihovny** jako sada uživatelského rozhraní jsou méně citlivé na rozbíjející změny v ovládacích prvcích.</span><span class="sxs-lookup"><span data-stu-id="dfd53-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="dfd53-116">Základní knihovny je odkazováno přímo v aplikaci koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="dfd53-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="dfd53-117">Pokud dojde k rozbíjející změny, Vývojář můžete aktualizovat na nejnovější verzi, nebo můžete upravit své aplikace pro spolupráci s narušující změně.</span><span class="sxs-lookup"><span data-stu-id="dfd53-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="dfd53-118">**PROVEĎTE ✔️** přemýšlení o použití knihovny.</span><span class="sxs-lookup"><span data-stu-id="dfd53-118">**✔️ DO** think about how your library will be used.</span></span> <span data-ttu-id="dfd53-119">Jaký vliv budou změny způsobující chyby mít na aplikací a knihoven, které ji používají?</span><span class="sxs-lookup"><span data-stu-id="dfd53-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="dfd53-120">**PROVEĎTE ✔️** minimalizovat změny způsobující chyby při vývoji nízké úrovně knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="dfd53-120">**✔️ DO** minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="dfd53-121">**✔️ ZVAŽTE** publikování hlavní přepsání knihovny jako nový balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="dfd53-121">**✔️ CONSIDER** publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="dfd53-122">Typy změny způsobující chyby</span><span class="sxs-lookup"><span data-stu-id="dfd53-122">Types of breaking changes</span></span>

<span data-ttu-id="dfd53-123">Zásadní změny se dělí do různých kategorií a nejsou rovnoměrně dopad.</span><span class="sxs-lookup"><span data-stu-id="dfd53-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="dfd53-124">Rozbíjející změny zdroje</span><span class="sxs-lookup"><span data-stu-id="dfd53-124">Source breaking change</span></span>

<span data-ttu-id="dfd53-125">Zdroj narušující změna nemá vliv na provádění programu, ale způsobí chyby při kompilaci, které se je znovu zkompilovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dfd53-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="dfd53-126">Například nová přetížení, můžete vytvořit nejednoznačnost volání metod, které byly dříve jednoznačný nebo přejmenováno parametr přeruší volajícím, které používají pojmenované parametry.</span><span class="sxs-lookup"><span data-stu-id="dfd53-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="dfd53-127">Protože zdroji narušující změna je škodlivých pouze když vývojáři znovu zkompilovat svých aplikací, je nejméně rušivé narušující změně.</span><span class="sxs-lookup"><span data-stu-id="dfd53-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="dfd53-128">Vývojáři můžete snadno vyřešit vlastní přerušeno zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="dfd53-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="dfd53-129">Rozbíjející změny chování</span><span class="sxs-lookup"><span data-stu-id="dfd53-129">Behavior breaking change</span></span>

<span data-ttu-id="dfd53-130">Změny chování jsou nejběžnějším typem rozbíjející změny: téměř všechny změny v chování, které by mohly narušit někdo.</span><span class="sxs-lookup"><span data-stu-id="dfd53-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="dfd53-131">Změny do knihovny, jako jsou podpisy metod výjimky vyvolána nebo vstupní nebo výstupní formáty dat, může všechny mít negativní vliv na zákazníky knihovny.</span><span class="sxs-lookup"><span data-stu-id="dfd53-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="dfd53-132">I oprava chyby kvalifikovat jako rozbíjející změny, pokud uživatelé spoléhali na dříve nefunkční chování.</span><span class="sxs-lookup"><span data-stu-id="dfd53-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="dfd53-133">Přidání funkcí a vylepšení chybné chování je dobrá věc, ale bez péče o to může být velmi obtížné pro stávající uživatele k upgradu.</span><span class="sxs-lookup"><span data-stu-id="dfd53-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="dfd53-134">Jedním z přístupů k pomáhá vývojářům řešit rozbíjející změny v chování je skrýt za nastavení.</span><span class="sxs-lookup"><span data-stu-id="dfd53-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="dfd53-135">Nastavení umožňují vývojářům aktualizovat na nejnovější verzi knihovny, zatímco ve stejnou dobu, zvolíte-li vyjádřit výslovný souhlas nebo vyjádřit výslovný nesouhlas rozbíjející změny.</span><span class="sxs-lookup"><span data-stu-id="dfd53-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="dfd53-136">Tato strategie umožňuje vývojářům dění přičemž umožníte jejich časově náročný kód upravit v čase.</span><span class="sxs-lookup"><span data-stu-id="dfd53-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="dfd53-137">Například technologie ASP.NET Core MVC má koncept [verze kompatibility](/aspnet/core/mvc/compatibility-version) aplikací, které mění funkcí aktivovaných a deaktivovaných na `MvcOptions`.</span><span class="sxs-lookup"><span data-stu-id="dfd53-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="dfd53-138">**✔️ ZVAŽTE** opuštění nové funkce ve výchozím nastavení, dojde k jejich vliv na stávající uživatele a umožňuje vývojářům vyjádřit výslovný souhlas s funkcí s nastavením.</span><span class="sxs-lookup"><span data-stu-id="dfd53-138">**✔️ CONSIDER** leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="dfd53-139">Binární zásadní změna</span><span class="sxs-lookup"><span data-stu-id="dfd53-139">Binary breaking change</span></span>

<span data-ttu-id="dfd53-140">Zásadní změna binární soubor se stane, když změníte veřejné rozhraní API knihovny, tak sestavení zkompilována proti starší verze knihovny není nadále možné volat rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="dfd53-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="dfd53-141">Například Změna signatury metody tak, že přidáte nový parametr způsobí, že sestavení, proti starší verzi knihovny vyvolávat <xref:System.MissingMethodException>.</span><span class="sxs-lookup"><span data-stu-id="dfd53-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="dfd53-142">Zásadní změna binární soubor může také dojít k narušení **celé sestavení**.</span><span class="sxs-lookup"><span data-stu-id="dfd53-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="dfd53-143">Přejmenování sestavení `AssemblyName` změní identitu sestavení, jako se přidání, odebrání nebo změna silný klíč názvů sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfd53-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="dfd53-144">Změna identity sestavení budou přerušeny všechny zkompilovaný kód, který se používá.</span><span class="sxs-lookup"><span data-stu-id="dfd53-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="dfd53-145">**❌ NEPODPORUJÍ** změnit název sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfd53-145">**❌ DO NOT** change an assembly name.</span></span>

<span data-ttu-id="dfd53-146">**❌ NEPODPORUJÍ** přidat, odebrat nebo změnit silného pojmenování klíče.</span><span class="sxs-lookup"><span data-stu-id="dfd53-146">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="dfd53-147">**✔️ ZVAŽTE** místo abstraktní základní třídy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dfd53-147">**✔️ CONSIDER** using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="dfd53-148">Přidání nic do rozhraní způsobí, že existující typy, které je implementují selhání.</span><span class="sxs-lookup"><span data-stu-id="dfd53-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="dfd53-149">Abstraktní základní třída umožňuje přidat výchozí virtuální implementace.</span><span class="sxs-lookup"><span data-stu-id="dfd53-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="dfd53-150">**✔️ ZVAŽTE** uvedení <xref:System.ObsoleteAttribute> na typy a členy, které máte v úmyslu odebrat.</span><span class="sxs-lookup"><span data-stu-id="dfd53-150">**✔️ CONSIDER** placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="dfd53-151">Pokyny pro aktualizaci kódu, aby již nebudete používat zastaralé rozhraní API by měl mít atribut.</span><span class="sxs-lookup"><span data-stu-id="dfd53-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="dfd53-152">Kód, který volá typy a metody s <xref:System.ObsoleteAttribute> zprávou zadaný pro atribut vygeneruje upozornění sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfd53-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="dfd53-153">Uživatelé dávající upozornění, kteří používají zastaralé rozhraní API zařízení surface čas k migraci tak, že je odebraný zastaralá rozhraní API, většina jsou jeho použití.</span><span class="sxs-lookup"><span data-stu-id="dfd53-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dfd53-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfd53-154">See also</span></span>

* [<span data-ttu-id="dfd53-155">Verze a aktualizace důležité informace pro vývojáře v C#</span><span class="sxs-lookup"><span data-stu-id="dfd53-155">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
* [<span data-ttu-id="dfd53-156">Úplnou příručku k rozhraní API rozbíjející změny v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="dfd53-156">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
* [<span data-ttu-id="dfd53-157">CoreFX narušující Změna pravidla</span><span class="sxs-lookup"><span data-stu-id="dfd53-157">CoreFX Breaking Change Rules</span></span>](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
[<span data-ttu-id="dfd53-158">Předchozí</span><span class="sxs-lookup"><span data-stu-id="dfd53-158">Previous</span></span>](./versioning.md)

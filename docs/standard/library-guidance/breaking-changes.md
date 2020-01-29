---
title: Přerušující změny a knihovny .NET
description: Doporučení osvědčených postupů pro navigaci při zásadních změnách při vytváření knihoven .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 2cbd9e0a818b52aede6c9b1f60fdf52dcbd7b96f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731465"
---
# <a name="breaking-changes"></a><span data-ttu-id="8569c-103">Změny způsobující chyby</span><span class="sxs-lookup"><span data-stu-id="8569c-103">Breaking changes</span></span>

<span data-ttu-id="8569c-104">Je důležité, aby knihovna .NET vyhledala rovnováhu mezi stabilitou stávajících uživatelů a inovací pro budoucnost.</span><span class="sxs-lookup"><span data-stu-id="8569c-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="8569c-105">Autoři knihoven se zabývat refaktoringem a přemýšlení kódu, dokud nebudou dokonalé, ale rozdělení stávajících uživatelů má negativní dopad, zejména pro knihovny nízké úrovně.</span><span class="sxs-lookup"><span data-stu-id="8569c-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="8569c-106">Typy projektů a průlomové změny</span><span class="sxs-lookup"><span data-stu-id="8569c-106">Project types and breaking changes</span></span>

<span data-ttu-id="8569c-107">Způsob, jakým komunita rozhraní .NET používá knihovnu, mění vliv na zásadní změny pro vývojáře koncových uživatelů.</span><span class="sxs-lookup"><span data-stu-id="8569c-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

- <span data-ttu-id="8569c-108">**Knihovny nízké úrovně a střední úrovně** , jako je serializátor, analyzátor HTML, databázový objekt – relační Mapovač nebo webové rozhraní, jsou ovlivněny zásadními změnami.</span><span class="sxs-lookup"><span data-stu-id="8569c-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="8569c-109">Stavební balíčky jsou používány vývojáři koncových uživatelů k vytváření aplikací a dalších knihoven jako závislostí NuGet.</span><span class="sxs-lookup"><span data-stu-id="8569c-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="8569c-110">Například vytváříte aplikaci a používáte Open sourceho klienta pro volání webové služby.</span><span class="sxs-lookup"><span data-stu-id="8569c-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="8569c-111">Zásadní aktualizace závislosti, kterou klient používá, není něco, co můžete opravit.</span><span class="sxs-lookup"><span data-stu-id="8569c-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="8569c-112">Je to open source klient, který je třeba změnit a nemáte nad ním žádnou kontrolu.</span><span class="sxs-lookup"><span data-stu-id="8569c-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="8569c-113">Je nutné najít kompatibilní verze knihoven nebo odeslat opravu klientské knihovně a počkat na novou verzi.</span><span class="sxs-lookup"><span data-stu-id="8569c-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="8569c-114">Nejhorším případem je, že chcete použít dvě knihovny, které závisejí na vzájemně nekompatibilní verzi třetí knihovny.</span><span class="sxs-lookup"><span data-stu-id="8569c-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

- <span data-ttu-id="8569c-115">**Knihovny vysoké úrovně** , jako je sada ovládacích prvků uživatelského rozhraní, jsou méně citlivé na přerušující změny.</span><span class="sxs-lookup"><span data-stu-id="8569c-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="8569c-116">Knihovny vysoké úrovně jsou přímo odkazovány v aplikaci koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="8569c-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="8569c-117">V případě, že dojde k zásadním změnám, může vývojář zvolit aktualizaci na nejnovější verzi nebo může upravit svou aplikaci tak, aby fungovala s průlomovou změnou.</span><span class="sxs-lookup"><span data-stu-id="8569c-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="8569c-118">✔️ se zamyslete nad tím, jak se vaše knihovna bude používat.</span><span class="sxs-lookup"><span data-stu-id="8569c-118">✔️ DO think about how your library will be used.</span></span> <span data-ttu-id="8569c-119">Jaký vliv budou tyto změny u aplikací a knihoven, které ji používají?</span><span class="sxs-lookup"><span data-stu-id="8569c-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="8569c-120">Při vývoji knihovny .NET nízké úrovně je ✔️ minimalizovat zásadní změny.</span><span class="sxs-lookup"><span data-stu-id="8569c-120">✔️ DO minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="8569c-121">✔️ Zvažte publikování většího přepsání knihovny jako nového balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="8569c-121">✔️ CONSIDER publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="8569c-122">Typy přerušujících změn</span><span class="sxs-lookup"><span data-stu-id="8569c-122">Types of breaking changes</span></span>

<span data-ttu-id="8569c-123">Zásadní změny spadají do různých kategorií a nejsou stejně ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="8569c-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="8569c-124">Změna konce zdroje</span><span class="sxs-lookup"><span data-stu-id="8569c-124">Source breaking change</span></span>

<span data-ttu-id="8569c-125">Zásadní změna zdroje neovlivní spuštění programu, ale způsobí chyby při kompilaci při příštím kompilování aplikace.</span><span class="sxs-lookup"><span data-stu-id="8569c-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="8569c-126">Například nové přetížení může vytvořit nejednoznačnost v voláních metody, které byly dříve dvojznačné, nebo přejmenovaný parametr způsobí přerušení volajících, které používají pojmenované parametry.</span><span class="sxs-lookup"><span data-stu-id="8569c-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="8569c-127">Vzhledem k tomu, že se změna zdrojového kódu neškodí jenom v případě, že vývojáři znovu zkompiluje své aplikace, je to nejmenší přerušení při změně.</span><span class="sxs-lookup"><span data-stu-id="8569c-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="8569c-128">Vývojáři můžou snadno opravit svůj vlastní poškozený zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="8569c-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="8569c-129">Změna narušení chování</span><span class="sxs-lookup"><span data-stu-id="8569c-129">Behavior breaking change</span></span>

<span data-ttu-id="8569c-130">Změny chování jsou nejběžnějším typem zásadní změny: téměř jakákoli změna v chování může poškodit někoho.</span><span class="sxs-lookup"><span data-stu-id="8569c-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="8569c-131">Změny v knihovně, jako jsou signatury metod, vyvolané výjimky nebo vstupní nebo výstupní datové formáty, by mohly mít negativní vliv na uživatele knihovny.</span><span class="sxs-lookup"><span data-stu-id="8569c-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="8569c-132">I Oprava chyby se může kvalifikovat jako zásadní změna, pokud se uživatelé spoléhali na dříve přerušené chování.</span><span class="sxs-lookup"><span data-stu-id="8569c-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="8569c-133">Přidání funkcí a vylepšení špatného chování je vhodné, ale bez péče může být pro stávající uživatele velmi obtížné provést upgrade.</span><span class="sxs-lookup"><span data-stu-id="8569c-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="8569c-134">Jedním ze způsobů, jak přispět vývojářům v práci s zásadními změnami chování, je skrýt ho za nastavením.</span><span class="sxs-lookup"><span data-stu-id="8569c-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="8569c-135">Nastavení umožní vývojářům aktualizace na nejnovější verzi vaší knihovny současně se zvolením možnosti výslovný souhlas nebo odhlášení nedostatku změn.</span><span class="sxs-lookup"><span data-stu-id="8569c-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="8569c-136">Tato strategie umožňuje vývojářům zůstat v aktuálním stavu, zatímco umožní přizpůsobovat jejich využívání kódu v průběhu času.</span><span class="sxs-lookup"><span data-stu-id="8569c-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="8569c-137">ASP.NET Core MVC má například koncept [verze kompatibility](/aspnet/core/mvc/compatibility-version) , který upravuje Funkce povolené a zakázané v `MvcOptions`.</span><span class="sxs-lookup"><span data-stu-id="8569c-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="8569c-138">✔️ Zvažte, že se ve výchozím nastavení vypnou nové funkce, pokud mají vliv na existující uživatele a umožní vývojářům, aby se k této funkci přihlásili pomocí nastavení.</span><span class="sxs-lookup"><span data-stu-id="8569c-138">✔️ CONSIDER leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="8569c-139">Změna binárního poškození</span><span class="sxs-lookup"><span data-stu-id="8569c-139">Binary breaking change</span></span>

<span data-ttu-id="8569c-140">K binárnímu poškození dojde, když změníte veřejné rozhraní API vaší knihovny, takže sestavení kompilována proti starším verzím knihovny již nebudou schopna volat rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8569c-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="8569c-141">Například změna signatury metody přidáním nového parametru způsobí, že sestavení zkompilované na starší verzi knihovny vyvolají <xref:System.MissingMethodException>.</span><span class="sxs-lookup"><span data-stu-id="8569c-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="8569c-142">Binární zásadní změna může také poškodit **celé sestavení**.</span><span class="sxs-lookup"><span data-stu-id="8569c-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="8569c-143">Přejmenováním sestavení pomocí `AssemblyName` dojde ke změně identity sestavení, protože se přidá, odebere nebo změní silný klíč pojmenování sestavení.</span><span class="sxs-lookup"><span data-stu-id="8569c-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="8569c-144">Změna identity sestavení způsobí přerušení veškerého zkompilovaného kódu, který ho používá.</span><span class="sxs-lookup"><span data-stu-id="8569c-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="8569c-145">❌ neměňte název sestavení.</span><span class="sxs-lookup"><span data-stu-id="8569c-145">❌ DO NOT change an assembly name.</span></span>

<span data-ttu-id="8569c-146">❌ Nepřidávat, odebírat ani měnit silný názvový klíč.</span><span class="sxs-lookup"><span data-stu-id="8569c-146">❌ DO NOT add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="8569c-147">✔️ Zvažte použití abstraktních základních tříd namísto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8569c-147">✔️ CONSIDER using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="8569c-148">Přidání cokoli do rozhraní způsobí, že existující typy, které ji implementují, selžou.</span><span class="sxs-lookup"><span data-stu-id="8569c-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="8569c-149">Abstraktní základní třída umožňuje přidat výchozí virtuální implementaci.</span><span class="sxs-lookup"><span data-stu-id="8569c-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="8569c-150">✔️ Zvažte umístění <xref:System.ObsoleteAttribute> na typy a členy, které chcete odebrat.</span><span class="sxs-lookup"><span data-stu-id="8569c-150">✔️ CONSIDER placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="8569c-151">Atribut by měl obsahovat pokyny pro aktualizaci kódu, aby již nepoužíval zastaralé rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8569c-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="8569c-152">Kód, který volá typy a metody s <xref:System.ObsoleteAttribute>, vygeneruje upozornění sestavení se zprávou poskytnutou atributu.</span><span class="sxs-lookup"><span data-stu-id="8569c-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="8569c-153">Upozornění dávají uživatelům, kteří používají zastaralý čas na ploše rozhraní API k migraci, takže po odebrání zastaralého rozhraní API už ho nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="8569c-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

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

<span data-ttu-id="8569c-154">✔️ Zajistěte, aby byly typy a metody s <xref:System.ObsoleteAttribute> po dobu neurčitou v knihovnách nízké úrovně a střední úrovně.</span><span class="sxs-lookup"><span data-stu-id="8569c-154">✔️ CONSIDER keeping types and methods with the <xref:System.ObsoleteAttribute> indefinitely in low and middle-level libraries.</span></span>

> <span data-ttu-id="8569c-155">Odebrání rozhraní API je binární zásadní změna.</span><span class="sxs-lookup"><span data-stu-id="8569c-155">Removing APIs is a binary breaking change.</span></span> <span data-ttu-id="8569c-156">Vzhledem k tomu, že udržování zastaralých typů a metod, pokud je zachování nízkých nákladů, nepřidává do knihovny velké množství technického dluhu.</span><span class="sxs-lookup"><span data-stu-id="8569c-156">Considering keeping obsolete types and methods if maintaining them is low cost and doesn't add lot of technical debt to your library.</span></span> <span data-ttu-id="8569c-157">Neodebrání typů a metod může přispět k tomu, abyste se vyhnuli nejhorším scénářům uvedeným výše.</span><span class="sxs-lookup"><span data-stu-id="8569c-157">Not removing types and methods can help avoid the worst-case scenarios mentioned above.</span></span>

## <a name="see-also"></a><span data-ttu-id="8569c-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8569c-158">See also</span></span>

- [<span data-ttu-id="8569c-159">Požadavky na verzi a aktualizace C# pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="8569c-159">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
- [<span data-ttu-id="8569c-160">Konečný průvodce pro změny v .NET v rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8569c-160">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [<span data-ttu-id="8569c-161">Rozhraní .NET – pravidla změny</span><span class="sxs-lookup"><span data-stu-id="8569c-161">.NET breaking change rules</span></span>](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="8569c-162">Předchozí</span><span class="sxs-lookup"><span data-stu-id="8569c-162">Previous</span></span>](versioning.md)

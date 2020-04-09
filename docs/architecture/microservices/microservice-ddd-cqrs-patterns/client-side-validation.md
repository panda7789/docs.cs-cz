---
title: Ověřování na straně klienta (ověřování v prezentačních vrstvách)
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Prozkoumejte klíčové koncepty ověřování na straně klienta.
ms.date: 10/08/2018
ms.openlocfilehash: 44c1e9fa280b19fcee87d4d1cdfcaa2ab9462f27
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988698"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="a8fa6-103">Ověřování na straně klienta (ověřování v prezentačních vrstvách)</span><span class="sxs-lookup"><span data-stu-id="a8fa6-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="a8fa6-104">I v případě, že zdrojem pravdy je model domény a nakonec musíte mít ověření na úrovni modelu domény, ověření lze stále zpracovávat na úrovni modelu domény (na straně serveru) a na straně ui (na straně klienta).</span><span class="sxs-lookup"><span data-stu-id="a8fa6-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the UI (client side).</span></span>

<span data-ttu-id="a8fa6-105">Ověření na straně klienta je pro uživatele velkým pohodlím.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="a8fa6-106">To šetří čas, který by jinak strávit čekání na zpáteční cestu na server, který by mohl vrátit chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="a8fa6-107">Z obchodního hlediska, i několik zlomků sekund násobí stokrát každý den přidává až hodně času, nákladů a frustrace.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="a8fa6-108">Jednoduché a okamžité ověření umožňuje uživatelům pracovat efektivněji a vytvářet kvalitnější vstupy a výstupy.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="a8fa6-109">Stejně jako model zobrazení a model domény se liší, zobrazení modelu ověřování a ověření modelu domény může být podobné, ale slouží jinému účelu.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="a8fa6-110">Pokud máte obavy o DRY (Don't Repeat Yourself princip), za to, že v tomto případě kód opětovné použití může také znamenat spojení, a v podnikových aplikacích je důležitější, aby pár straně serveru na straně klienta, než dodržovat princip DRY.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-110">If you are concerned about DRY (the Don't Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="a8fa6-111">I při použití ověření na straně klienta byste měli vždy ověřit příkazy nebo vstupní dtovací v kódu serveru, protože serverová api jsou možným vektorem útoku.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="a8fa6-112">Obvykle, dělá obojí je vaše nejlepší sázka, protože pokud máte klientskou aplikaci, z hlediska Uživatelského rozhraní, to je nejlepší být proaktivní a nedovolit uživateli zadat neplatné informace.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="a8fa6-113">Proto v kódu na straně klienta obvykle ověřit ViewModels.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="a8fa6-114">Můžete také ověřit výstup klienta DTO nebo příkazy před jejich odesláním do služeb.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="a8fa6-115">Implementace ověření na straně klienta závisí na tom, jaký druh klientské aplikace vytváříte.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="a8fa6-116">Bude to jiné, pokud ověřujete data ve webové webové aplikaci MVC s většinou kódu v rozhraní .NET, webové aplikace SPA s tímto ověřením kódovaném v Jazyce JavaScript nebo TypeScript nebo mobilní aplikace kódovaná xamarinem a c#.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, a SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a8fa6-117">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="a8fa6-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="a8fa6-118">Ověření v mobilních aplikacích Xamarin</span><span class="sxs-lookup"><span data-stu-id="a8fa6-118">Validation in Xamarin mobile apps</span></span>

- <span data-ttu-id="a8fa6-119">**Ověřit zadávání textu a zobrazit chyby** </span><span class="sxs-lookup"><span data-stu-id="a8fa6-119">**Validate Text Input and Show Errors** </span></span>\
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- <span data-ttu-id="a8fa6-120">**Zpětné volání ověření** </span><span class="sxs-lookup"><span data-stu-id="a8fa6-120">**Validation Callback** </span></span>\
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="a8fa6-121">Ověření v aplikacích ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a8fa6-121">Validation in ASP.NET Core apps</span></span>

- <span data-ttu-id="a8fa6-122">**Rick Anderson. Přidání ověření** </span><span class="sxs-lookup"><span data-stu-id="a8fa6-122">**Rick Anderson. Adding validation** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="a8fa6-123">Ověření ve webových aplikacích SPA (Úhlové 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="a8fa6-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

- <span data-ttu-id="a8fa6-124">**Ado Kukic. Ověřování formuláře úhlové 2** </span><span class="sxs-lookup"><span data-stu-id="a8fa6-124">**Ado Kukic. Angular 2 Form Validation** </span></span>\
  <https://scotch.io/tutorials/angular-2-form-validation>

- <span data-ttu-id="a8fa6-125">**Ověření formuláře** </span><span class="sxs-lookup"><span data-stu-id="a8fa6-125">**Form Validation** </span></span>\
  <https://angular.io/guide/form-validation>

- <span data-ttu-id="a8fa6-126">**Ověření.**</span><span class="sxs-lookup"><span data-stu-id="a8fa6-126">**Validation.**</span></span> <span data-ttu-id="a8fa6-127">Breeze dokumentace.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-127">Breeze documentation.</span></span> \
  <https://breeze.github.io/doc-js/validation.html>

<span data-ttu-id="a8fa6-128">Stručně řečeno, jedná se o nejdůležitější pojmy, pokud jde o validaci:</span><span class="sxs-lookup"><span data-stu-id="a8fa6-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="a8fa6-129">Entity a agregace by měly vynucovat vlastní konzistenci a být "vždy platné".</span><span class="sxs-lookup"><span data-stu-id="a8fa6-129">Entities and aggregates should enforce their own consistency and be "always valid".</span></span> <span data-ttu-id="a8fa6-130">Agregační kořeny jsou zodpovědné za konzistenci více entit v rámci stejného agregace.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="a8fa6-131">Pokud se domníváte, že entita potřebuje zadat neplatný stav, zvažte použití jiného objektového modelu – například pomocí dočasného objektu DTO, dokud nevytvoříte konečnou entitu domény.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="a8fa6-132">Pokud potřebujete vytvořit několik souvisejících objektů, jako je například agregace, a jsou platné pouze po vytvoření všech, zvažte použití vzoru Factory.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="a8fa6-133">Ve většině případů s redundantní ověření na straně klienta je dobré, protože aplikace může být proaktivní.</span><span class="sxs-lookup"><span data-stu-id="a8fa6-133">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a8fa6-134">[Předchozí](domain-model-layer-validations.md)
>[další](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="a8fa6-134">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>

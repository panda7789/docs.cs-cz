---
title: Ověřování na straně klienta (ověřování v prezentačních vrstvách)
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Prozkoumejte klíčové koncepty ověřování na straně klienta.
ms.date: 10/08/2018
ms.openlocfilehash: 4e72dcafafc3144a75afe1fd23a4a779f5667459
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295995"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="db15b-103">Ověřování na straně klienta (ověřování v prezentačních vrstvách)</span><span class="sxs-lookup"><span data-stu-id="db15b-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="db15b-104">I když je zdrojem pravdy model domény a nakonec musíte mít ověření na úrovni doménového modelu, může se ověřování stále zpracovávat na úrovni doménového modelu (na straně serveru) i v uživatelském rozhraní (na straně klienta).</span><span class="sxs-lookup"><span data-stu-id="db15b-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the UI (client side).</span></span>

<span data-ttu-id="db15b-105">Ověřování na straně klienta je pro uživatele vynikajícím pohodlím.</span><span class="sxs-lookup"><span data-stu-id="db15b-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="db15b-106">Šetří čas, který by jinak stráví čekáním na zpoždění odezvy na server, který může vracet chyby ověřování.</span><span class="sxs-lookup"><span data-stu-id="db15b-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="db15b-107">V obchodních termínech, dokonce i pár sekund vynásobených stovkami časů, se každý den přidává až do hodně času, nákladů a frustrace.</span><span class="sxs-lookup"><span data-stu-id="db15b-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="db15b-108">Jednoduché a okamžité ověření umožňuje uživatelům pracovat efektivněji a vytvářet lepší kvalitu vstupu a výstupu.</span><span class="sxs-lookup"><span data-stu-id="db15b-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="db15b-109">Stejně jako model zobrazení a doménový model se liší, zobrazení ověření modelu a ověřování modelu domény může být podobné, ale slouží k jinému účelu.</span><span class="sxs-lookup"><span data-stu-id="db15b-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="db15b-110">Pokud máte obavy o vysušení (princip "Neopakuj se" principu), zvažte, že v tomto případě opětovného použití kódu může také znamenat propojení a v podnikových aplikacích je důležitější, aby nemohlo být spojen se serverem na straně klienta, než aby následoval za SUCHÝm principem.</span><span class="sxs-lookup"><span data-stu-id="db15b-110">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="db15b-111">I když používáte ověřování na straně klienta, měli byste vždy ověřit příkazy nebo vstupní DTO v kódu serveru, protože rozhraní API serveru představují možný vektor útoku.</span><span class="sxs-lookup"><span data-stu-id="db15b-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="db15b-112">Většinou je nejlepší tip, protože pokud máte klientskou aplikaci, z perspektivy uživatelského prostředí je nejlepší být aktivní a neumožníte uživateli zadat neplatné informace.</span><span class="sxs-lookup"><span data-stu-id="db15b-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="db15b-113">Proto v kódu na straně klienta, který obvykle ověřujete ViewModels.</span><span class="sxs-lookup"><span data-stu-id="db15b-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="db15b-114">Před odesláním do služeb můžete také ověřit výstupní DTO nebo příkazy klienta.</span><span class="sxs-lookup"><span data-stu-id="db15b-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="db15b-115">Implementace ověřování na straně klienta závisí na typu klientské aplikace, kterou vytváříte.</span><span class="sxs-lookup"><span data-stu-id="db15b-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="db15b-116">Bude se lišit v případě, že ověřujete data ve webové aplikaci webové MVC s většinou kódu v rozhraní .NET, Webová aplikace SPA s tímto ověřováním je kódována v JavaScriptu nebo TypeScript nebo mobilní aplikace kódované pomocí Xamarin a C#.</span><span class="sxs-lookup"><span data-stu-id="db15b-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, a SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="db15b-117">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="db15b-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="db15b-118">Ověřování v mobilních aplikacích Xamarin</span><span class="sxs-lookup"><span data-stu-id="db15b-118">Validation in Xamarin mobile apps</span></span>

- <span data-ttu-id="db15b-119">**Ověřit zadání textu a zobrazit chyby** </span><span class="sxs-lookup"><span data-stu-id="db15b-119">**Validate Text Input and Show Errors** </span></span>\
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- <span data-ttu-id="db15b-120">**Zpětné volání ověřování** </span><span class="sxs-lookup"><span data-stu-id="db15b-120">**Validation Callback** </span></span>\
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="db15b-121">Ověřování v ASP.NET Corech aplikacích</span><span class="sxs-lookup"><span data-stu-id="db15b-121">Validation in ASP.NET Core apps</span></span>

- <span data-ttu-id="db15b-122">**Rick Anderson. Přidání ověřování** </span><span class="sxs-lookup"><span data-stu-id="db15b-122">**Rick Anderson. Adding validation** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="db15b-123">Ověřování v ZABEZPEČENých webových aplikacích (úhlové 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="db15b-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

- <span data-ttu-id="db15b-124">**ADO KuKic. 2. úhlové ověření formuláře** </span><span class="sxs-lookup"><span data-stu-id="db15b-124">**Ado Kukic. Angular 2 Form Validation** </span></span>\
  <https://scotch.io/tutorials/angular-2-form-validation>

- <span data-ttu-id="db15b-125">**Ověření formuláře** </span><span class="sxs-lookup"><span data-stu-id="db15b-125">**Form Validation** </span></span>\
  <https://angular.io/guide/form-validation>

- <span data-ttu-id="db15b-126">**Export.**</span><span class="sxs-lookup"><span data-stu-id="db15b-126">**Validation.**</span></span> <span data-ttu-id="db15b-127">Dokumentaci k Breeze.</span><span class="sxs-lookup"><span data-stu-id="db15b-127">Breeze documentation.</span></span> \
  <https://breeze.github.io/doc-js/validation.html>

<span data-ttu-id="db15b-128">V souhrnu se jedná o nejdůležitější pojmy týkající se ověřování:</span><span class="sxs-lookup"><span data-stu-id="db15b-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="db15b-129">Entity a agregace by měly vymáhat svou vlastní konzistenci a být "vždy platné".</span><span class="sxs-lookup"><span data-stu-id="db15b-129">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="db15b-130">Agregované kořeny jsou zodpovědné za konzistenci více entit v rámci stejné agregace.</span><span class="sxs-lookup"><span data-stu-id="db15b-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="db15b-131">Pokud se domníváte, že entita potřebuje zadat neplatný stav, zvažte použití jiného objektového modelu – například pomocí dočasného DTO, dokud nevytvoříte konečnou entitu domény.</span><span class="sxs-lookup"><span data-stu-id="db15b-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="db15b-132">Pokud potřebujete vytvořit několik souvisejících objektů, například agregaci a jsou platné pouze po vytvoření všech z nich, zvažte použití modelu továrny.</span><span class="sxs-lookup"><span data-stu-id="db15b-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="db15b-133">Ve většině případů je vhodné, aby bylo redundantní ověřování na straně klienta dobré, protože aplikace může být aktivní.</span><span class="sxs-lookup"><span data-stu-id="db15b-133">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="db15b-134">[Předchozí](domain-model-layer-validations.md)Další
>[](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="db15b-134">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>

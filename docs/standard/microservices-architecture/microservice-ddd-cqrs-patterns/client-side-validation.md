---
title: Ověřování na straně klienta (ověřování v prezentačních vrstvách)
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Seznamte se s klíčové koncepty ověřování na straně klienta.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 0b4bef8c80f26cea5552d4f59468811ae1f18a8d
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58462796"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="f9254-103">Ověřování na straně klienta (ověřování v prezentačních vrstvách)</span><span class="sxs-lookup"><span data-stu-id="f9254-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="f9254-104">I v případě, že je zdroj pravdivých informací doménový model a nakonec musí mít ověření na úrovni modelu domény, můžete ověření dosud zpracovány na úrovni modelu domény (na straně serveru) a uživatelského rozhraní (na straně klienta).</span><span class="sxs-lookup"><span data-stu-id="f9254-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the UI (client side).</span></span>

<span data-ttu-id="f9254-105">Ověřování na straně klienta je skvělé usnadnění práce pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="f9254-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="f9254-106">To šetří čas, který byste jinak strávili čekání na odezvu na server, který může vrátit chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="f9254-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="f9254-107">V obchodní termíny dokonce i pár zlomky sekund vynásobené opakovaném každý den dohromady tvoří spoustu času, expense a frustrace.</span><span class="sxs-lookup"><span data-stu-id="f9254-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="f9254-108">Jednoduché a okamžité ověřování umožňuje uživatelům vyšší efektivity práce a vytvářet lepší kvalitu vstupu a výstupu.</span><span class="sxs-lookup"><span data-stu-id="f9254-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="f9254-109">Stejně jako model zobrazení a modelu domény se liší, ověření modelu zobrazení a ověření modelu domény může být podobné, ale pro jiný účel.</span><span class="sxs-lookup"><span data-stu-id="f9254-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="f9254-110">Pokud máte obavy o zkušební (není opakujte sami zásada), vezměte v úvahu, že v tomto případě opakované využívání kódu může také znamenat párování a v oddílu podnikové aplikace je více důležité, abyste na straně klienta než postupujte podle principu suchého spárovat na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="f9254-110">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="f9254-111">I při použití ověřování na straně klienta, by měla vždy ověřování příkazům nebo vstupní DTO v serverovém kódu, protože server rozhraní API jsou možné útoku.</span><span class="sxs-lookup"><span data-stu-id="f9254-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="f9254-112">Provádění obou je obvykle nejlepší tip vzhledem k tomu, že pokud máte klientské aplikace z pohledu uživatelského prostředí, je nejlepší a provádět proaktivně, aby uživatel zadal neplatné informace.</span><span class="sxs-lookup"><span data-stu-id="f9254-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="f9254-113">Proto v kódu na straně klienta je obvykle ověřit modely ViewModel.</span><span class="sxs-lookup"><span data-stu-id="f9254-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="f9254-114">Může také ověřit klienta výstup DTO nebo příkazy před jejich odesláním do služby.</span><span class="sxs-lookup"><span data-stu-id="f9254-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="f9254-115">Implementace ověřování na straně klienta, závisí na druhu klientskou aplikaci, kterou vytváříte.</span><span class="sxs-lookup"><span data-stu-id="f9254-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="f9254-116">Bude jiný, jsou ověřování dat ve webovém webové aplikace MVC s největším počtem kód v .NET, webové aplikace SPA pomocí tohoto ověřování je zakódovaný v jazyce JavaScript nebo TypeScript, nebo kódované mobilní aplikace pomocí Xamarinu a C#.</span><span class="sxs-lookup"><span data-stu-id="f9254-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, an SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f9254-117">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="f9254-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="f9254-118">Ověření v mobilních aplikacích Xamarin</span><span class="sxs-lookup"><span data-stu-id="f9254-118">Validation in Xamarin mobile apps</span></span>

- <span data-ttu-id="f9254-119">**Ověření textový vstup a zobrazit chyby** \\</span><span class="sxs-lookup"><span data-stu-id="f9254-119">**Validate Text Input and Show Errors** \\</span></span>
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- <span data-ttu-id="f9254-120">**Zpětné volání pro ověření** \\</span><span class="sxs-lookup"><span data-stu-id="f9254-120">**Validation Callback** \\</span></span>
  [https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="f9254-121">Ověření v aplikacích ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f9254-121">Validation in ASP.NET Core apps</span></span>

- <span data-ttu-id="f9254-122">**Rick Anderson. Přidání ověřování** \\</span><span class="sxs-lookup"><span data-stu-id="f9254-122">**Rick Anderson. Adding validation** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="f9254-123">Ověřování do aplikace SPA webové aplikace (Angular 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="f9254-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

- <span data-ttu-id="f9254-124">**Ado Kukic. Ověřování angular 2 formuláře** \\</span><span class="sxs-lookup"><span data-stu-id="f9254-124">**Ado Kukic. Angular 2 Form Validation** \\</span></span>
  [https://scotch.io/tutorials/angular-2-form-validation](https://scotch.io/tutorials/angular-2-form-validation)

- <span data-ttu-id="f9254-125">**Ověření formuláře** \\</span><span class="sxs-lookup"><span data-stu-id="f9254-125">**Form Validation** \\</span></span>
  [https://angular.io/docs/ts/latest/cookbook/form-validation.html](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

- <span data-ttu-id="f9254-126">**Ověření.**</span><span class="sxs-lookup"><span data-stu-id="f9254-126">**Validation.**</span></span> <span data-ttu-id="f9254-127">Dokumentace k podrobným.</span><span class="sxs-lookup"><span data-stu-id="f9254-127">Breeze documentation.</span></span> \
  [https://breeze.github.io/doc-js/validation.html](https://breeze.github.io/doc-js/validation.html)

<span data-ttu-id="f9254-128">Stručně řečeno jedná se ty nejdůležitější koncepty související s ověření:</span><span class="sxs-lookup"><span data-stu-id="f9254-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="f9254-129">Entity a agregace by měl vynutit vlastní konzistenci a "vždy platný".</span><span class="sxs-lookup"><span data-stu-id="f9254-129">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="f9254-130">Agregační kořeny zodpovídají za víc entitami konzistenci v rámci stejné agregace.</span><span class="sxs-lookup"><span data-stu-id="f9254-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="f9254-131">Pokud se domníváte, že entita musí zadat neplatném stavu, zvažte použití jiného objektu modelu, například pomocí dočasný objekt DTO, dokud nevytvoříte entita domény posledním.</span><span class="sxs-lookup"><span data-stu-id="f9254-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="f9254-132">Pokud je potřeba vytvořit několik souvisejících objektů, jako jsou agregace, a že jsou platné jenom po jejich vytvoření, zvažte použití vzoru objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="f9254-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="f9254-133">Ve většině případů redundantní ověřování na straně klienta je dobré, vzhledem k tomu, že aplikace může být aktivní.</span><span class="sxs-lookup"><span data-stu-id="f9254-133">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f9254-134">[Předchozí](domain-model-layer-validations.md)
>[další](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="f9254-134">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>
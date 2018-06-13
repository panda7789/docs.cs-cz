---
title: Ověřování na straně klienta (ověřování v prezentační vrstvy)
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Ověřování na straně klienta (ověřování v prezentační vrstvy)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 2adce39561dd2b97910155ebed595a2df7785c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574670"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="86cb9-103">Ověřování na straně klienta (ověřování v prezentační vrstvy)</span><span class="sxs-lookup"><span data-stu-id="86cb9-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="86cb9-104">I v případě, že je zdroj založená modelu domény a nakonec musí mít ověření na úrovni modelu domény, můžete ověření dosud zpracovány na úrovni modelu domény (na straně serveru) i na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="86cb9-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the client side.</span></span>

<span data-ttu-id="86cb9-105">Ověřování na straně klienta je velmi užitečný pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="86cb9-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="86cb9-106">Ho šetří čas, které by jinak tráví čekání na dobu odezvy na server, který může znovu objevit chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="86cb9-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="86cb9-107">V obchodní podmínky dokonce i pár zlomků sekund násobí stokrát každý den přidá do velké množství času, náklady a před.</span><span class="sxs-lookup"><span data-stu-id="86cb9-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="86cb9-108">Snadný a okamžitou ověření umožňuje uživatelům vyšší efektivity práce a vytvořit lepší kvalitu vstup a výstup.</span><span class="sxs-lookup"><span data-stu-id="86cb9-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="86cb9-109">Stejně jako v zobrazení modelu a modelu domény se liší, může být podobné ale pro jiný účel ověření modelu zobrazení a ověření modelu domény.</span><span class="sxs-lookup"><span data-stu-id="86cb9-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="86cb9-110">Pokud máte obavy o SUCHÝ (nemáte opakujte sami zásada), vezměte v úvahu, v takovém případě může znamenat opakované použití kódu také párování a v podnikové aplikace, které je důležitější nechcete na straně klienta než postupujte podle SUCHÝCH Princip spojte na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="86cb9-110">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="86cb9-111">I při použití ověřování na straně klienta, si vždy ověřte příkazech nebo vstupní DTOs v serverovém kódu, protože rozhraní API serveru je možný útok.</span><span class="sxs-lookup"><span data-stu-id="86cb9-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="86cb9-112">Provádění obou je obvykle nejlepším řešením vzhledem k tomu, že pokud máte klientské aplikace, z hlediska činnosti koncového uživatele je nejvhodnější proaktivní a není povolena, aby uživatel zadal neplatné informace.</span><span class="sxs-lookup"><span data-stu-id="86cb9-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="86cb9-113">Proto v kódu na straně klienta je obvykle ověřit ViewModels.</span><span class="sxs-lookup"><span data-stu-id="86cb9-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="86cb9-114">Může také ověřit klienta výstup DTOs nebo příkazy před jejich odesláním do služby.</span><span class="sxs-lookup"><span data-stu-id="86cb9-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="86cb9-115">Implementace ověřování na straně klienta, závisí na jaký druh klientskou aplikaci, kterou vytváříte.</span><span class="sxs-lookup"><span data-stu-id="86cb9-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="86cb9-116">Bude jiný, jsou ověřování dat v web webová aplikace MVC s většinou kód v rozhraní .NET, webové aplikace služby Zabezpečené ověřování HESLA s že ověřování probíhá programového v JavaScript nebo TypeScript, nebo mobilní aplikace programového s Xamarinem a C\#.</span><span class="sxs-lookup"><span data-stu-id="86cb9-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, an SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C\#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="86cb9-117">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="86cb9-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="86cb9-118">Ověření v mobilních aplikacích Xamarin</span><span class="sxs-lookup"><span data-stu-id="86cb9-118">Validation in Xamarin mobile apps</span></span>

-   <span data-ttu-id="86cb9-119">**Ověření vstupní Text a zobrazit chyby**
    [*https://developer.xamarin.com/recipes/ios/standard\_ovládací prvky nebo textu\_pole nebo ověřit\_vstupní /*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span><span class="sxs-lookup"><span data-stu-id="86cb9-119">**Validate Text Input and Show Errors**
[*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span></span>

-   <span data-ttu-id="86cb9-120">**Zpětné volání pro ověření**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span><span class="sxs-lookup"><span data-stu-id="86cb9-120">**Validation Callback**
[*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span></span>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="86cb9-121">Ověření v aplikacích ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="86cb9-121">Validation in ASP.NET Core apps</span></span>

-   <span data-ttu-id="86cb9-122">**Rick Anderson. Přidání ověřování**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="86cb9-122">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="86cb9-123">Ověření v SPA webové aplikace (úhlová 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="86cb9-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

-   <span data-ttu-id="86cb9-124">**ADO Kukic. Úhlová ověřování 2 formuláře** **
    **[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span><span class="sxs-lookup"><span data-stu-id="86cb9-124">**Ado Kukic. Angular 2 Form Validation** **
**[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span></span>

-   <span data-ttu-id="86cb9-125">**Ověření formuláře**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span><span class="sxs-lookup"><span data-stu-id="86cb9-125">**Form Validation**
[*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span></span>

-   <span data-ttu-id="86cb9-126">**Ověření.**</span><span class="sxs-lookup"><span data-stu-id="86cb9-126">**Validation.**</span></span> <span data-ttu-id="86cb9-127">Dokumentace uloženy.</span><span class="sxs-lookup"><span data-stu-id="86cb9-127">Breeze documentation.</span></span>
    [*https://breeze.github.io/doc-js/validation.html*](https://breeze.github.io/doc-js/validation.html)

<span data-ttu-id="86cb9-128">V souhrnu jsou to nejdůležitější koncepty namapoval ověření:</span><span class="sxs-lookup"><span data-stu-id="86cb9-128">In summary, these are the most important concepts in regards to validation:</span></span>

-   <span data-ttu-id="86cb9-129">Entity a agregace by měl vynutit vlastní konzistence a "vždy platný".</span><span class="sxs-lookup"><span data-stu-id="86cb9-129">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="86cb9-130">Agregační kořeny jsou zodpovědní za konzistence více entit v rámci stejné agregace.</span><span class="sxs-lookup"><span data-stu-id="86cb9-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

-   <span data-ttu-id="86cb9-131">Pokud si myslíte, že entita musí zadat neplatném stavu, zvažte použití různých objektový model – například pomocí dočasné DTO, dokud nevytvoříte entita konečné domény.</span><span class="sxs-lookup"><span data-stu-id="86cb9-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

-   <span data-ttu-id="86cb9-132">Pokud je potřeba vytvořit několik souvisejících objektů, jako je například agregace, a jsou pouze platné po všechny z nich byly vytvořeny, zvažte použití vzoru objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="86cb9-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

-   <span data-ttu-id="86cb9-133">Ověřování rozhraní jsou nejvhodnější konkrétní vrstvy, jako je například prezentační vrstvy nebo vrstvě služba nebo aplikace, ale obvykle není v vrstva modelu domény, protože by musela být silné závislý na představuje rozhraní infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="86cb9-133">Validation frameworks are best used in specific layers, such as the presentation layer or the application/service layer, but usually not in the domain model layer, because you would need to take a strong dependency on an infrastructure framework.</span></span>

-   <span data-ttu-id="86cb9-134">S redundantní ověřování na straně klienta je vhodný, ve většině případů, protože aplikace může být aktivní.</span><span class="sxs-lookup"><span data-stu-id="86cb9-134">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="86cb9-135">[Předchozí] (domény modelu layer-validations.md) [Další] (domain události návrhu implementation.md)</span><span class="sxs-lookup"><span data-stu-id="86cb9-135">[Previous] (domain-model-layer-validations.md) [Next] (domain-events-design-implementation.md)</span></span>

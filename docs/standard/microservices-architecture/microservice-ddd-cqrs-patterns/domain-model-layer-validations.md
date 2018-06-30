---
title: Navrhování ověření ve vrstvě modelu domény.
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Navrhování ověření ve vrstvě modelu domény.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c071d269977ccecea9a7d4d79da78d7967bb1618
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105732"
---
# <a name="designing-validations-in-the-domain-model-layer"></a><span data-ttu-id="32820-103">Navrhování ověření ve vrstvě modelu domény.</span><span class="sxs-lookup"><span data-stu-id="32820-103">Designing validations in the domain model layer</span></span>

<span data-ttu-id="32820-104">V DDD může být ověřovacích pravidel představit jako výstupních podmínek.</span><span class="sxs-lookup"><span data-stu-id="32820-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="32820-105">Hlavní zodpovědností agregace je vynutit výstupních podmínek napříč změny stavu pro všechny entity v rámci této agregace.</span><span class="sxs-lookup"><span data-stu-id="32820-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="32820-106">Entity domény by mělo být vždy platný entity.</span><span class="sxs-lookup"><span data-stu-id="32820-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="32820-107">Existují počet výstupních podmínek pro objekt, který by měl mít vždy hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="32820-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="32820-108">Například objekt pořadí položek vždy musí mít množství, které musí být kladné celé číslo a název článku a cena.</span><span class="sxs-lookup"><span data-stu-id="32820-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="32820-109">Proto výstupních podmínek vynucení má na starosti entit domény (zejména o agregační root) a objekt entity neměli mít možnost existovat, aniž by musel být platný.</span><span class="sxs-lookup"><span data-stu-id="32820-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="32820-110">Výchozí pravidla se jednoduše vyjádřený jako kontrakty a výjimky nebo oznámení se vyvolá, když se porušení.</span><span class="sxs-lookup"><span data-stu-id="32820-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="32820-111">Zdůvodnění to je, že mnoho chyb dojít, protože jsou objekty ve stavu, který by měl mít nikdy nebyla v.</span><span class="sxs-lookup"><span data-stu-id="32820-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="32820-112">Toto je dobré vysvětlení z Gregu Young v [online diskusní](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span><span class="sxs-lookup"><span data-stu-id="32820-112">The following is a good explanation from Greg Young in an [online discussion](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="32820-113">Umožňuje navrhnout, že máme teď SendUserCreationEmailService, která přijímá UserProfile... jak můžete jsme zefektivní v této službě, že název není null?</span><span class="sxs-lookup"><span data-stu-id="32820-113">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="32820-114">Jsme ji znovu zkontrolujte?</span><span class="sxs-lookup"><span data-stu-id="32820-114">Do we check it again?</span></span> <span data-ttu-id="32820-115">Nebo vyšší pravděpodobnost... právě se nemáte Nepokoušejte se zkontrolovat a "Naděje pro nejlepší" – naděje někdo bothered k ověření před odesláním pro vás.</span><span class="sxs-lookup"><span data-stu-id="32820-115">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="32820-116">Samozřejmě použití vývoje řízeného Testováním jeden první testů, které jsme být zápis, je, že pokud poslat zákazníkovi s hodnotou null názvem, aby měli vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="32820-116">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="32820-117">Ale po jsme začali psát tyto druhy testy opakovaně jsme zjistili... "Počkejte Pokud jsme nikdy název stane null jsme nemohli mají všechny tyto testy"</span><span class="sxs-lookup"><span data-stu-id="32820-117">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implementing-validations-in-the-domain-model-layer"></a><span data-ttu-id="32820-118">Implementace ověření ve vrstvě modelu domény.</span><span class="sxs-lookup"><span data-stu-id="32820-118">Implementing validations in the domain model layer</span></span>

<span data-ttu-id="32820-119">Ověření se většinou implementují v konstruktorech entita domény nebo metody, které lze aktualizaci entity.</span><span class="sxs-lookup"><span data-stu-id="32820-119">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="32820-120">K implementaci ověření, například ověřování dat a aktivaci výjimky, pokud se ověření nezdaří několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="32820-120">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="32820-121">Existují také pokročilejší vzory, třeba pomocí vzoru specifikace pro ověření a v oznámení vzoru má vracet kolekci chyby místo vrací výjimku pro každé ověření, protože k ní dojde.</span><span class="sxs-lookup"><span data-stu-id="32820-121">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validating-conditions-and-throwing-exceptions"></a><span data-ttu-id="32820-122">Ověřování podmínky a vyvolávání výjimek</span><span class="sxs-lookup"><span data-stu-id="32820-122">Validating conditions and throwing exceptions</span></span>

<span data-ttu-id="32820-123">Následující příklad kódu zobrazuje nejjednodušším přístupem při ověřování v entita domény podle vyvolání k výjimce.</span><span class="sxs-lookup"><span data-stu-id="32820-123">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="32820-124">V tabulce odkazy na konci této části zobrazíte odkazy na pokročilejší implementace podle vzorů, které jsme dříve popsané.</span><span class="sxs-lookup"><span data-stu-id="32820-124">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="32820-125">Lepší příkladu by ukazují, je třeba zajistit, že se nezměnila vnitřní stav, nebo že došlo k všechny mutací pro metodu.</span><span class="sxs-lookup"><span data-stu-id="32820-125">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="32820-126">Například následující implementaci ponecháte objekt v neplatném stavu:</span><span class="sxs-lookup"><span data-stu-id="32820-126">For example, the following implementation would leave the object in an invalid state:</span></span>

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shipingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

<span data-ttu-id="32820-127">Pokud hodnota stavu je neplatná, první řádek adresy a Město již byly změněny.</span><span class="sxs-lookup"><span data-stu-id="32820-127">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="32820-128">Adresa pro které by mohly způsobit neplatná.</span><span class="sxs-lookup"><span data-stu-id="32820-128">That might make the address invalid.</span></span>

<span data-ttu-id="32820-129">Podobný postup lze použít v konstruktoru entity, vyvolá výjimku, abyste měli jistotu, že tato entita je platný po vytvoření.</span><span class="sxs-lookup"><span data-stu-id="32820-129">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="32820-130">Pomocí ověřování atributů v modelu, podle datových poznámek</span><span class="sxs-lookup"><span data-stu-id="32820-130">Using validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="32820-131">Další možností je použití atributů ověření podle datových poznámek.</span><span class="sxs-lookup"><span data-stu-id="32820-131">Another approach is to use validation attributes based on data annotations.</span></span> <span data-ttu-id="32820-132">Atributy ověření zadejte způsob, jak nakonfigurovat ověření modelu, který se koncepčně podobá ověření na pole v tabulkách databáze.</span><span class="sxs-lookup"><span data-stu-id="32820-132">Validation attributes provide a way to configure model validation, which is similar conceptually to validation on fields in database tables.</span></span> <span data-ttu-id="32820-133">To zahrnuje omezení, jako je například přiřazení datových typů nebo povinná pole.</span><span class="sxs-lookup"><span data-stu-id="32820-133">This includes constraints such as assigning data types or required fields.</span></span> <span data-ttu-id="32820-134">Ostatní typy ověření, které zahrnuje použití vzorce k datům a vynutit obchodních pravidel, jako je číslo platební karty, telefonní číslo nebo e-mailovou adresu.</span><span class="sxs-lookup"><span data-stu-id="32820-134">Other types of validation include applying patterns to data to enforce business rules, such as a credit card number, phone number, or email address.</span></span> <span data-ttu-id="32820-135">Atributy ověření usnadňují vynucují požadavky.</span><span class="sxs-lookup"><span data-stu-id="32820-135">Validation attributes make it easy to enforce requirements.</span></span>

<span data-ttu-id="32820-136">Ale, jak je znázorněno v následujícím kódu, tento přístup může být příliš rušivý v modelu DDD, protože má závislost na ModelState.IsValid z Microsoft.AspNetCore.Mvc.ModelState, které je třeba volat z řadičů MVC.</span><span class="sxs-lookup"><span data-stu-id="32820-136">However, as shown in the following code, this approach might be too intrusive in a DDD model, because it takes a dependency on ModelState.IsValid from Microsoft.AspNetCore.Mvc.ModelState, which you must call from your MVC controllers.</span></span> <span data-ttu-id="32820-137">Ověření modelu proběhne před každou volaná akce kontroleru a metoda kontroleru odpovídá kontrolovat výsledek volání ModelState.IsValid a náležitě reagovat.</span><span class="sxs-lookup"><span data-stu-id="32820-137">The model validation occurs prior to each controller action being invoked, and it is the controller method’s responsibility to inspect the result of calling ModelState.IsValid and react appropriately.</span></span> <span data-ttu-id="32820-138">Rozhodnout a použít ho závisí na tom úzce párované chcete modelu, který má být s tuto infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="32820-138">The decision to use it depends on how tightly coupled you want the model to be with that infrastructure.</span></span>

```csharp
using System.ComponentModel.DataAnnotations;
// Other using statements ...
// Entity is a custom base class which has the ID
public class Product : Entity
{
    [Required]
    [StringLength(100)]
    public string Title { get; private set; }

    [Required]
    [Range(0, 999.99)]
    public decimal Price { get; private set; }

    [Required]
    [VintageProduct(1970)]
    [DataType(DataType.Date)]
    public DateTime ReleaseDate { get; private set; }

    [Required]
    [StringLength(1000)]
    public string Description { get; private set; }

    // Constructor...
    // Additional methods for entity logic and constructor...
}
```

<span data-ttu-id="32820-139">Však z DDD hlediska, modelu domény je lepší je ponechat štíhlého s použití výjimek v metodách chování vaší entity, nebo implementace vzorů specifikace a oznámení k vynucení pravidel ověřování.</span><span class="sxs-lookup"><span data-stu-id="32820-139">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span> <span data-ttu-id="32820-140">Ověření architektury, jako je datových poznámek v ASP.NET Core nebo jiných rozhraní ověření jako FluentValidation provádění požadavku k vyvolání rozhraní.</span><span class="sxs-lookup"><span data-stu-id="32820-140">Validation frameworks like data annotations in ASP.NET Core or any other validation frameworks like FluentValidation carry a requirement to invoke the application framework.</span></span> <span data-ttu-id="32820-141">Například při volání metody ModelState.IsValid v datových poznámek, budete muset vyvolání řadiče ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="32820-141">For example, when calling the ModelState.IsValid method in data annotations, you need to invoke ASP.NET controllers.</span></span>

<span data-ttu-id="32820-142">Můžete ho mít smysl použití datové poznámky na aplikační vrstvu v třídách ViewModel (namísto domény entity), která bude přijímat vstup, aby bylo možné ověření modelu v rámci uživatelského rozhraní vrstvy.</span><span class="sxs-lookup"><span data-stu-id="32820-142">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="32820-143">Ale to neměli dělat na vyloučení ověření v rámci modelu domény.</span><span class="sxs-lookup"><span data-stu-id="32820-143">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="32820-144">Ověřování entity implementací vzoru specifikaci a vzoru oznámení</span><span class="sxs-lookup"><span data-stu-id="32820-144">Validating entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="32820-145">Nakonec komplikovanějších přístup k ověření, které implementují v modelu domény je implementací vzoru specifikace ve spojení s vzoru oznámení, jak je popsáno v některé další zdroje najdete dál.</span><span class="sxs-lookup"><span data-stu-id="32820-145">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="32820-146">Je důležité zmínit, že můžete taky právě jeden z těchto vzory – například ověřování ručně s řídicí příkazy, ale pomocí vzoru oznámení zásobníku a vrátíte se seznamu chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="32820-146">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="using-deferred-validation-in-the-domain"></a><span data-ttu-id="32820-147">Pomocí odložené ověřování v doméně</span><span class="sxs-lookup"><span data-stu-id="32820-147">Using deferred validation in the domain</span></span>

<span data-ttu-id="32820-148">Existují různé přístupy k řešení odložené ověření v doméně.</span><span class="sxs-lookup"><span data-stu-id="32820-148">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="32820-149">V jeho kniha [Implementing Domain-Driven návrhu](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon popisuje v části na ověření.</span><span class="sxs-lookup"><span data-stu-id="32820-149">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="32820-150">Dvoustupňové ověření</span><span class="sxs-lookup"><span data-stu-id="32820-150">Two-step validation</span></span>

<span data-ttu-id="32820-151">Zvažte také dvoustupňové ověření.</span><span class="sxs-lookup"><span data-stu-id="32820-151">Also consider two-step validation.</span></span> <span data-ttu-id="32820-152">Použijte ověření na úrovni pole v příkazu objekty přenos dat (DTOs) a na úrovni domény ověření uvnitř vaší entity.</span><span class="sxs-lookup"><span data-stu-id="32820-152">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="32820-153">Můžete k tomu vrácením výsledný objekt místo výjimky abyste snadněji řešit chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="32820-153">You can do this by returning a result object instead exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="32820-154">Pomocí pole ověřování s anotacemi dat, například můžete není duplicitní ověření definice.</span><span class="sxs-lookup"><span data-stu-id="32820-154">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="32820-155">Spuštění, ale může být současně na straně serveru a na straně klienta v případě DTOs (příkazy a ViewModels, například).</span><span class="sxs-lookup"><span data-stu-id="32820-155">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="32820-156">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="32820-156">Additional resources</span></span>

-   <span data-ttu-id="32820-157">**Rachel Appel. Úvod k ověření modelu v aplikaci ASP.NET MVC jádra**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span><span class="sxs-lookup"><span data-stu-id="32820-157">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC**
[*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span></span>

-   <span data-ttu-id="32820-158">**Rick Anderson. Přidání ověřování**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="32820-158">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

-   <span data-ttu-id="32820-159">**Martin Fowler. Nahrazení vyvolání výjimky s oznámení v ověření**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span><span class="sxs-lookup"><span data-stu-id="32820-159">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations**
[*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span></span>

-   <span data-ttu-id="32820-160">**Specifikace a vzory oznámení**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span><span class="sxs-lookup"><span data-stu-id="32820-160">**Specification and Notification Patterns**
[*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span></span>

-   <span data-ttu-id="32820-161">**Lev Gorodinski. Ověřování v doméně řízené návrhu (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span><span class="sxs-lookup"><span data-stu-id="32820-161">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)**
[*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span></span>

-   <span data-ttu-id="32820-162">**Colin konektoru. Ověření modelu domény**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span><span class="sxs-lookup"><span data-stu-id="32820-162">**Colin Jack. Domain Model Validation**
[*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span></span>

-   <span data-ttu-id="32820-163">**Jimmy Bogard. Ověření DDD světě**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span><span class="sxs-lookup"><span data-stu-id="32820-163">**Jimmy Bogard. Validation in a DDD world**
[*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="32820-164">[Předchozí](enumeration-classes-over-enum-types.md)
[další](client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="32820-164">[Previous](enumeration-classes-over-enum-types.md)
[Next](client-side-validation.md)</span></span>

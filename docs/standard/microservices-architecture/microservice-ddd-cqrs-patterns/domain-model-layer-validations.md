---
title: Návrh ověřování ve vrstvě doménového modelu
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Návrh ověřování ve vrstvě doménového modelu
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 6ff325bb062da2ebff815fc847d2247707a0bf7f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188050"
---
# <a name="designing-validations-in-the-domain-model-layer"></a><span data-ttu-id="279c6-103">Návrh ověřování ve vrstvě doménového modelu</span><span class="sxs-lookup"><span data-stu-id="279c6-103">Designing validations in the domain model layer</span></span>

<span data-ttu-id="279c6-104">V DDD ověřovacích pravidel si lze představit jako výstupních podmínek.</span><span class="sxs-lookup"><span data-stu-id="279c6-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="279c6-105">Hlavní zodpovědností agregace je vynucovat změny stavu pro všechny entity v rámci této agregaci výstupních podmínek.</span><span class="sxs-lookup"><span data-stu-id="279c6-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="279c6-106">Domény entity musí být vždy platný entity.</span><span class="sxs-lookup"><span data-stu-id="279c6-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="279c6-107">Existuje je určitý počet výstupních podmínek pro objekt, který by měl mít hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="279c6-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="279c6-108">Například objekt pořadí položek má vždy mít množství, které musí být kladné celé číslo a název článku a ceny.</span><span class="sxs-lookup"><span data-stu-id="279c6-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="279c6-109">Proto zodpovídá za vynucování výstupních podmínek entit domény (zejména z agregační root) a objekt entity by neměla být schopná existovat bez platné.</span><span class="sxs-lookup"><span data-stu-id="279c6-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="279c6-110">Výchozí pravidla se jednoduše vyjádřený jako smluv a výjimky nebo oznámení jsou vyvolány, když je porušena.</span><span class="sxs-lookup"><span data-stu-id="279c6-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="279c6-111">Zdůvodnění to je, že mnoho chyb dojít, protože objekty jsou ve stavu, který by měl mít nikdy nebyla v.</span><span class="sxs-lookup"><span data-stu-id="279c6-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="279c6-112">Tady je dobrý popis z Grega Younga: v [diskuse](https://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span><span class="sxs-lookup"><span data-stu-id="279c6-112">The following is a good explanation from Greg Young in an [online discussion](https://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="279c6-113">Navrhnout Řekněme, že nyní máme SendUserCreationEmailService, která přebírá... UserProfile jak můžete jsme racionalizovat dané služby, název není null?</span><span class="sxs-lookup"><span data-stu-id="279c6-113">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="279c6-114">Zkontrolujeme ho znovu?</span><span class="sxs-lookup"><span data-stu-id="279c6-114">Do we check it again?</span></span> <span data-ttu-id="279c6-115">Nebo vyšší pravděpodobnost... je právě není Nepokoušejte se ke kontrole a "doufat těch nejlepších" – Doufáme, že někdo bothered abyste ověřili, že před odesláním.</span><span class="sxs-lookup"><span data-stu-id="279c6-115">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="279c6-116">Samozřejmě použití vývoje Řízeného, jeden první testů, které jsme se zápis, je, že pokud poslat zákazníkovi s názvem hodnotu null, že by měla vyvolat chybu.</span><span class="sxs-lookup"><span data-stu-id="279c6-116">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="279c6-117">Ale když jsme začali psát tyto druhy testů tytéž Uvědomujeme... "Počkejte, pokud jsme název se může nikdy null by máme všechny tyto testy"</span><span class="sxs-lookup"><span data-stu-id="279c6-117">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implementing-validations-in-the-domain-model-layer"></a><span data-ttu-id="279c6-118">Implementace ověření ve vrstvě doménového modelu</span><span class="sxs-lookup"><span data-stu-id="279c6-118">Implementing validations in the domain model layer</span></span>

<span data-ttu-id="279c6-119">Ověření jsou obvykle implementovány v konstruktorech entita domény nebo v metodách, které můžete aktualizovat entitu.</span><span class="sxs-lookup"><span data-stu-id="279c6-119">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="279c6-120">Existuje několik způsobů, jak implementovat ověřování, jako je například ověřování dat a vyvolání výjimky, pokud se ověření nezdaří.</span><span class="sxs-lookup"><span data-stu-id="279c6-120">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="279c6-121">Existují také pokročilejší vzory, třeba pomocí vzoru specifikace pro ověření a vzor oznámení k vrácení kolekce chyb místo vrácení výjimky pro každé ověření, protože k ní dojde.</span><span class="sxs-lookup"><span data-stu-id="279c6-121">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validating-conditions-and-throwing-exceptions"></a><span data-ttu-id="279c6-122">Ověření podmínek a vyvolávání výjimek</span><span class="sxs-lookup"><span data-stu-id="279c6-122">Validating conditions and throwing exceptions</span></span>

<span data-ttu-id="279c6-123">Následující příklad kódu ukazuje nejjednodušším přístupem k ověření v entita domény vyvoláním výjimky.</span><span class="sxs-lookup"><span data-stu-id="279c6-123">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="279c6-124">V tabulce odkazy na konci této části se zobrazí odkazy na pokročilejší implementací na základě vzorců, které mají jsme probírali dříve.</span><span class="sxs-lookup"><span data-stu-id="279c6-124">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="279c6-125">Lepší příkladu by ukazují, je potřeba zajistit, že se nezměnil vnitřní stav, nebo že došlo k všechny mutace pro metodu.</span><span class="sxs-lookup"><span data-stu-id="279c6-125">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="279c6-126">Například následující implementaci zůstane objekt v neplatném stavu:</span><span class="sxs-lookup"><span data-stu-id="279c6-126">For example, the following implementation would leave the object in an invalid state:</span></span>

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

<span data-ttu-id="279c6-127">Pokud je neplatná hodnota stavu, první řádek adresy a Město již byly změněny.</span><span class="sxs-lookup"><span data-stu-id="279c6-127">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="279c6-128">Adresa pro, který může být neplatný.</span><span class="sxs-lookup"><span data-stu-id="279c6-128">That might make the address invalid.</span></span>

<span data-ttu-id="279c6-129">Podobný přístup je možné v konstruktoru entity, vyvolá výjimku, abyste měli jistotu, že entita je platný po jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="279c6-129">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="279c6-130">Pomocí atributů ověření v modelu, podle datových poznámek</span><span class="sxs-lookup"><span data-stu-id="279c6-130">Using validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="279c6-131">Další možností je použití atributů ověření založené na datových poznámek.</span><span class="sxs-lookup"><span data-stu-id="279c6-131">Another approach is to use validation attributes based on data annotations.</span></span> <span data-ttu-id="279c6-132">Ověření atributy poskytují způsob, jak konfigurovat ověření modelu, které se koncepčně podobá ověření na pole v databázové tabulky.</span><span class="sxs-lookup"><span data-stu-id="279c6-132">Validation attributes provide a way to configure model validation, which is similar conceptually to validation on fields in database tables.</span></span> <span data-ttu-id="279c6-133">To zahrnuje omezení, jako je například přiřazení datových typů nebo povinná pole.</span><span class="sxs-lookup"><span data-stu-id="279c6-133">This includes constraints such as assigning data types or required fields.</span></span> <span data-ttu-id="279c6-134">Jiné typy ověření, které zahrnuje použití vzorců k datům a vynucování obchodních pravidel, jako je číslo platební karty, telefonní číslo nebo e-mailovou adresu.</span><span class="sxs-lookup"><span data-stu-id="279c6-134">Other types of validation include applying patterns to data to enforce business rules, such as a credit card number, phone number, or email address.</span></span> <span data-ttu-id="279c6-135">Ověřování atributů usnadňují vynucují požadavky.</span><span class="sxs-lookup"><span data-stu-id="279c6-135">Validation attributes make it easy to enforce requirements.</span></span>

<span data-ttu-id="279c6-136">Ale jak je znázorněno v následujícím kódu, tento přístup může být příliš nežádoucí v modelu DDD, protože to je závislá na ModelState.IsValid z Microsoft.AspNetCore.Mvc.ModelState, které je nutné volat z vašeho řadiče MVC.</span><span class="sxs-lookup"><span data-stu-id="279c6-136">However, as shown in the following code, this approach might be too intrusive in a DDD model, because it takes a dependency on ModelState.IsValid from Microsoft.AspNetCore.Mvc.ModelState, which you must call from your MVC controllers.</span></span> <span data-ttu-id="279c6-137">Ověření modelu nastává před každou volaná akce kontroleru a zodpovídá za metoda kontroleru ke kontrole výsledku volání ModelState.IsValid a reagují odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="279c6-137">The model validation occurs prior to each controller action being invoked, and it is the controller method’s responsibility to inspect the result of calling ModelState.IsValid and react appropriately.</span></span> <span data-ttu-id="279c6-138">Závisí na tom, rozhodnout a použít ho úzce párované chcete modelu, který má být s tuto infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="279c6-138">The decision to use it depends on how tightly coupled you want the model to be with that infrastructure.</span></span>

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

<span data-ttu-id="279c6-139">Nicméně z DDD hlediska, doménový model nejlépe, zůstane lean se použití výjimek v metodách chování vaší entity, nebo prostřednictvím implementace vzorů specifikaci a oznámení k vynucení pravidel ověřování.</span><span class="sxs-lookup"><span data-stu-id="279c6-139">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span> <span data-ttu-id="279c6-140">Ověření architektury, jako jsou datové poznámky v ASP.NET Core nebo jakékoli jiné ověření architektur, jako třeba FluentValidation provádění požadavku k vyvolání aplikační platformu.</span><span class="sxs-lookup"><span data-stu-id="279c6-140">Validation frameworks like data annotations in ASP.NET Core or any other validation frameworks like FluentValidation carry a requirement to invoke the application framework.</span></span> <span data-ttu-id="279c6-141">Například při volání metody ModelState.IsValid anotacemi dat, budete muset vyvolat kontrolery ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="279c6-141">For example, when calling the ModelState.IsValid method in data annotations, you need to invoke ASP.NET controllers.</span></span>

<span data-ttu-id="279c6-142">Může být vhodné k použití anotací dat v aplikační vrstvě v tříd ViewModel (namísto domény entity), které bude přijímat vstup, aby se ověření modelu ve vrstvě uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="279c6-142">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="279c6-143">Ale to by neměl být provedeno v vyloučení ověřování v rámci modelu domény.</span><span class="sxs-lookup"><span data-stu-id="279c6-143">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="279c6-144">Ověřování entity díky implementaci vzoru specifikaci a vzor oznámení</span><span class="sxs-lookup"><span data-stu-id="279c6-144">Validating entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="279c6-145">Nakonec komplikovanějších přístupem k implementaci ověření v doménovém modelu je implementace vzoru specifikace ve spojení se vzorem oznámení, jak je vysvětleno v některé z dalších prostředků najdete dál.</span><span class="sxs-lookup"><span data-stu-id="279c6-145">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="279c6-146">Stojí za zmínku, že můžete použít také pouze jedna z těchto vzorců – například ověřování ručně řídicí příkazy, ale pomocí vzoru oznámení do zásobníku a vrátí seznam chyb při ověřování.</span><span class="sxs-lookup"><span data-stu-id="279c6-146">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="using-deferred-validation-in-the-domain"></a><span data-ttu-id="279c6-147">Použití odložené ověřování v doméně</span><span class="sxs-lookup"><span data-stu-id="279c6-147">Using deferred validation in the domain</span></span>

<span data-ttu-id="279c6-148">Existují různé přístupy k řešení odložené ověření v doméně.</span><span class="sxs-lookup"><span data-stu-id="279c6-148">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="279c6-149">Ve své knize [Implementing Domain-Driven návrhu](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon probírají v části v ověřování.</span><span class="sxs-lookup"><span data-stu-id="279c6-149">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="279c6-150">Dvoustupňové ověřování</span><span class="sxs-lookup"><span data-stu-id="279c6-150">Two-step validation</span></span>

<span data-ttu-id="279c6-151">Zvažte také dvoustupňové ověření.</span><span class="sxs-lookup"><span data-stu-id="279c6-151">Also consider two-step validation.</span></span> <span data-ttu-id="279c6-152">V příkazu objekty přenosu dat (DTO) a ověřování na úrovni domény uvnitř vaší entity pomocí ověření na úrovni pole.</span><span class="sxs-lookup"><span data-stu-id="279c6-152">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="279c6-153">Můžete to provést tak, že vrací objekt výsledku místo výjimek pro snazší řešení chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="279c6-153">You can do this by returning a result object instead exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="279c6-154">Pomocí pole ověřování s anotacemi dat, například nereplikujete ověření definice.</span><span class="sxs-lookup"><span data-stu-id="279c6-154">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="279c6-155">Provádění, ale může být na straně serveru a klienta v případě DTO (příkazy a modely ViewModels, například).</span><span class="sxs-lookup"><span data-stu-id="279c6-155">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="279c6-156">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="279c6-156">Additional resources</span></span>

-   <span data-ttu-id="279c6-157">**Rachel Appel. Úvod k ověření modelu v ASP.NET Core MVC**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span><span class="sxs-lookup"><span data-stu-id="279c6-157">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC**
[*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span></span>

-   <span data-ttu-id="279c6-158">**Rick Anderson. Přidání ověřování**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="279c6-158">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

-   <span data-ttu-id="279c6-159">**Martina Fowlera. Nahrazení vyvolávání výjimek s oznámením v ověření**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span><span class="sxs-lookup"><span data-stu-id="279c6-159">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations**
[*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span></span>

-   <span data-ttu-id="279c6-160">**Specifikace a vzory oznámení**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span><span class="sxs-lookup"><span data-stu-id="279c6-160">**Specification and Notification Patterns**
[*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span></span>

-   <span data-ttu-id="279c6-161">**Lev Gorodinski. Ověřování v návrhu řízeného doménou (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span><span class="sxs-lookup"><span data-stu-id="279c6-161">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)**
[*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span></span>

-   <span data-ttu-id="279c6-162">**Colin konektoru. Ověření modelu domény**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span><span class="sxs-lookup"><span data-stu-id="279c6-162">**Colin Jack. Domain Model Validation**
[*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span></span>

-   <span data-ttu-id="279c6-163">**Jimmy Bogard. Ověření ve světě DDD**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span><span class="sxs-lookup"><span data-stu-id="279c6-163">**Jimmy Bogard. Validation in a DDD world**
[*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="279c6-164">[Předchozí](enumeration-classes-over-enum-types.md)
[další](client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="279c6-164">[Previous](enumeration-classes-over-enum-types.md)
[Next](client-side-validation.md)</span></span>

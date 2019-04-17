---
title: Návrh ověřování ve vrstvě doménového modelu
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Klíčové koncepce ověření modelu domény.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: ae1252f4544f184a5f63ef02ba898da9b4373e17
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612703"
---
# <a name="design-validations-in-the-domain-model-layer"></a><span data-ttu-id="80ffa-103">Návrh ověřování ve vrstvě doménového modelu</span><span class="sxs-lookup"><span data-stu-id="80ffa-103">Design validations in the domain model layer</span></span>

<span data-ttu-id="80ffa-104">V DDD ověřovacích pravidel si lze představit jako výstupních podmínek.</span><span class="sxs-lookup"><span data-stu-id="80ffa-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="80ffa-105">Hlavní zodpovědností agregace je vynucovat změny stavu pro všechny entity v rámci této agregaci výstupních podmínek.</span><span class="sxs-lookup"><span data-stu-id="80ffa-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="80ffa-106">Domény entity musí být vždy platný entity.</span><span class="sxs-lookup"><span data-stu-id="80ffa-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="80ffa-107">Existuje je určitý počet výstupních podmínek pro objekt, který by měl mít hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="80ffa-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="80ffa-108">Například objekt pořadí položek má vždy mít množství, které musí být kladné celé číslo a název článku a ceny.</span><span class="sxs-lookup"><span data-stu-id="80ffa-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="80ffa-109">Proto zodpovídá za vynucování výstupních podmínek entit domény (zejména z agregační root) a objekt entity by neměla být schopná existovat bez platné.</span><span class="sxs-lookup"><span data-stu-id="80ffa-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="80ffa-110">Výchozí pravidla se jednoduše vyjádřený jako smluv a výjimky nebo oznámení jsou vyvolány, když je porušena.</span><span class="sxs-lookup"><span data-stu-id="80ffa-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="80ffa-111">Zdůvodnění to je, že mnoho chyb dojít, protože objekty jsou ve stavu, který by měl mít nikdy nebyla v.</span><span class="sxs-lookup"><span data-stu-id="80ffa-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="80ffa-112">Tady je dobrý popis z Grega Younga: v [diskuse](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/):</span><span class="sxs-lookup"><span data-stu-id="80ffa-112">The following is a good explanation from Greg Young in an [online discussion](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="80ffa-113">Navrhnout Řekněme, že nyní máme SendUserCreationEmailService, která přebírá... UserProfile jak můžete jsme racionalizovat dané služby, název není null?</span><span class="sxs-lookup"><span data-stu-id="80ffa-113">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="80ffa-114">Zkontrolujeme ho znovu?</span><span class="sxs-lookup"><span data-stu-id="80ffa-114">Do we check it again?</span></span> <span data-ttu-id="80ffa-115">Nebo vyšší pravděpodobnost... je právě není Nepokoušejte se ke kontrole a "doufat těch nejlepších" – Doufáme, že někdo bothered abyste ověřili, že před odesláním.</span><span class="sxs-lookup"><span data-stu-id="80ffa-115">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="80ffa-116">Samozřejmě použití vývoje Řízeného, jeden první testů, které jsme se zápis, je, že pokud poslat zákazníkovi s názvem hodnotu null, že by měla vyvolat chybu.</span><span class="sxs-lookup"><span data-stu-id="80ffa-116">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="80ffa-117">Ale když jsme začali psát tyto druhy testů tytéž Uvědomujeme... "Počkejte, pokud jsme název se může nikdy null by máme všechny tyto testy"</span><span class="sxs-lookup"><span data-stu-id="80ffa-117">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implement-validations-in-the-domain-model-layer"></a><span data-ttu-id="80ffa-118">Implementace ověřování ve vrstvě doménového modelu</span><span class="sxs-lookup"><span data-stu-id="80ffa-118">Implement validations in the domain model layer</span></span>

<span data-ttu-id="80ffa-119">Ověření jsou obvykle implementovány v konstruktorech entita domény nebo v metodách, které můžete aktualizovat entitu.</span><span class="sxs-lookup"><span data-stu-id="80ffa-119">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="80ffa-120">Existuje několik způsobů, jak implementovat ověřování, jako je například ověřování dat a vyvolání výjimky, pokud se ověření nezdaří.</span><span class="sxs-lookup"><span data-stu-id="80ffa-120">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="80ffa-121">Existují také pokročilejší vzory, třeba pomocí vzoru specifikace pro ověření a vzor oznámení k vrácení kolekce chyb místo vrácení výjimky pro každé ověření, protože k ní dojde.</span><span class="sxs-lookup"><span data-stu-id="80ffa-121">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validate-conditions-and-throw-exceptions"></a><span data-ttu-id="80ffa-122">Ověření podmínek a vyvolávat výjimky</span><span class="sxs-lookup"><span data-stu-id="80ffa-122">Validate conditions and throw exceptions</span></span>

<span data-ttu-id="80ffa-123">Následující příklad kódu ukazuje nejjednodušším přístupem k ověření v entita domény vyvoláním výjimky.</span><span class="sxs-lookup"><span data-stu-id="80ffa-123">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="80ffa-124">V tabulce odkazy na konci této části se zobrazí odkazy na pokročilejší implementací na základě vzorců, které mají jsme probírali dříve.</span><span class="sxs-lookup"><span data-stu-id="80ffa-124">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="80ffa-125">Lepší příkladu by ukazují, je potřeba zajistit, že se nezměnil vnitřní stav, nebo že došlo k všechny mutace pro metodu.</span><span class="sxs-lookup"><span data-stu-id="80ffa-125">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="80ffa-126">Například následující implementaci zůstane objekt v neplatném stavu:</span><span class="sxs-lookup"><span data-stu-id="80ffa-126">For example, the following implementation would leave the object in an invalid state:</span></span>

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shippingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

<span data-ttu-id="80ffa-127">Pokud je neplatná hodnota stavu, první řádek adresy a Město již byly změněny.</span><span class="sxs-lookup"><span data-stu-id="80ffa-127">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="80ffa-128">Adresa pro, který může být neplatný.</span><span class="sxs-lookup"><span data-stu-id="80ffa-128">That might make the address invalid.</span></span>

<span data-ttu-id="80ffa-129">Podobný přístup je možné v konstruktoru entity, vyvolá výjimku, abyste měli jistotu, že entita je platný po jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="80ffa-129">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="80ffa-130">Použití atributů ověření v modelu na základě dat poznámky</span><span class="sxs-lookup"><span data-stu-id="80ffa-130">Use validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="80ffa-131">Anotací dat, jako jsou požadované nebo MaxLength atributy lze použít ke konfiguraci vlastností pole databáze EF Core, jak je podrobně popsaný v části [mapování tabulky](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) oddílu, ale [už nebude fungovat pro entitu ověřování v EF Core](https://github.com/aspnet/EntityFrameworkCore/issues/3680) (ani nemá <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> metoda), jak to máte všechno od EF v rozhraní .NET Framework 4.x.</span><span class="sxs-lookup"><span data-stu-id="80ffa-131">Data annotations, like the Required or MaxLength attributes, can be used to configure EF Core database field properties, as explained in detail in the [Table mapping](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) section, but [they no longer work for entity validation in EF Core](https://github.com/aspnet/EntityFrameworkCore/issues/3680) (neither does the <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> method), as they have done since EF 4.x in .NET Framework.</span></span>

<span data-ttu-id="80ffa-132">Datové poznámky a <xref:System.ComponentModel.DataAnnotations.IValidatableObject> rozhraní je stále možné k ověření modelu během vazby modelu, před vyvolání akce kontroleru obvyklým způsobem, ale je model určen ViewModel nebo objekt DTO a, který je MVC nebo rozhraní API není doménový model žádný problém.</span><span class="sxs-lookup"><span data-stu-id="80ffa-132">Data annotations and the <xref:System.ComponentModel.DataAnnotations.IValidatableObject> interface can still be used for model validation during model binding, prior to the controller’s actions invocation as usual, but that model is meant to be a ViewModel or DTO and that’s an MVC or API concern not a domain model concern.</span></span>

<span data-ttu-id="80ffa-133">Po provedení koncepční rozdíly vymazat, můžete dál používat datových poznámek a `IValidatableObject` ve třídě entity pro ověření, pokud vaše akce zobrazí parametr objektu entity třídy, což se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="80ffa-133">Having made the conceptual difference clear, you can still use data annotations and `IValidatableObject` in the entity class for validation, if your actions receive an entity class object parameter, which is not recommended.</span></span> <span data-ttu-id="80ffa-134">V takovém případě dojde k ověření při vazby modelu, těsně před vyvolání akce a můžete zkontrolovat vlastnost ModelState.IsValid kontroleru zkontrolujte výsledek, ale pak znovu dojde v kontroleru, ne před uložením objektu entity v Kontext databáze, protože provedli od EF 4.x.</span><span class="sxs-lookup"><span data-stu-id="80ffa-134">In that case, validation will occur upon model binding, just before invoking the action and you can check the controller’s ModelState.IsValid property to check the result, but then again, it happens in the controller, not before persisting the entity object in the DbContext, as it had done since EF 4.x.</span></span>

<span data-ttu-id="80ffa-135">Stále můžete implementovat vlastní ověřování ve třídě entity pomocí datových poznámek a `IValidatableObject.Validate` metodu tak, že přepíšete metodu SaveChanges DbContext.</span><span class="sxs-lookup"><span data-stu-id="80ffa-135">You can still implement custom validation in the entity class using data annotations and the `IValidatableObject.Validate` method, by overriding the DbContext’s SaveChanges method.</span></span>

<span data-ttu-id="80ffa-136">Zobrazí se ukázková implementace pro ověření `IValidatableObject` entity v [tento komentář na Githubu](https://github.com/aspnet/EntityFrameworkCore/issues/3680#issuecomment-155502539).</span><span class="sxs-lookup"><span data-stu-id="80ffa-136">You can see a sample implementation for validating `IValidatableObject` entities in [this comment on GitHub](https://github.com/aspnet/EntityFrameworkCore/issues/3680#issuecomment-155502539).</span></span> <span data-ttu-id="80ffa-137">Ukázky neprovádí ověřování založených na atributech, ale měly by být snadno se implementuje pomocí reflexe ve stejném přepsání.</span><span class="sxs-lookup"><span data-stu-id="80ffa-137">That sample doesn’t do attribute-based validations, but they should be easy to implement using reflection in the same override.</span></span>

<span data-ttu-id="80ffa-138">Nicméně z DDD hlediska, doménový model nejlépe, zůstane lean se použití výjimek v metodách chování vaší entity, nebo prostřednictvím implementace vzorů specifikaci a oznámení k vynucení pravidel ověřování.</span><span class="sxs-lookup"><span data-stu-id="80ffa-138">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span>

<span data-ttu-id="80ffa-139">Může být vhodné k použití anotací dat v aplikační vrstvě v tříd ViewModel (namísto domény entity), které bude přijímat vstup, aby se ověření modelu ve vrstvě uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="80ffa-139">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="80ffa-140">Ale to by neměl být provedeno v vyloučení ověřování v rámci modelu domény.</span><span class="sxs-lookup"><span data-stu-id="80ffa-140">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="80ffa-141">Ověření entity díky implementaci vzoru specifikaci a vzor oznámení</span><span class="sxs-lookup"><span data-stu-id="80ffa-141">Validate entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="80ffa-142">Nakonec komplikovanějších přístupem k implementaci ověření v doménovém modelu je implementace vzoru specifikace ve spojení se vzorem oznámení, jak je vysvětleno v některé z dalších prostředků najdete dál.</span><span class="sxs-lookup"><span data-stu-id="80ffa-142">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="80ffa-143">Stojí za zmínku, že můžete použít také pouze jedna z těchto vzorců – například ověřování ručně řídicí příkazy, ale pomocí vzoru oznámení do zásobníku a vrátí seznam chyb při ověřování.</span><span class="sxs-lookup"><span data-stu-id="80ffa-143">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="use-deferred-validation-in-the-domain"></a><span data-ttu-id="80ffa-144">Používají odložené ověřování v doméně</span><span class="sxs-lookup"><span data-stu-id="80ffa-144">Use deferred validation in the domain</span></span>

<span data-ttu-id="80ffa-145">Existují různé přístupy k řešení odložené ověření v doméně.</span><span class="sxs-lookup"><span data-stu-id="80ffa-145">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="80ffa-146">Ve své knize [Implementing Domain-Driven návrhu](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon probírají v části v ověřování.</span><span class="sxs-lookup"><span data-stu-id="80ffa-146">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="80ffa-147">Dvoustupňové ověřování</span><span class="sxs-lookup"><span data-stu-id="80ffa-147">Two-step validation</span></span>

<span data-ttu-id="80ffa-148">Zvažte také dvoustupňové ověření.</span><span class="sxs-lookup"><span data-stu-id="80ffa-148">Also consider two-step validation.</span></span> <span data-ttu-id="80ffa-149">V příkazu objekty přenosu dat (DTO) a ověřování na úrovni domény uvnitř vaší entity pomocí ověření na úrovni pole.</span><span class="sxs-lookup"><span data-stu-id="80ffa-149">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="80ffa-150">Můžete to provést tak, že vrací objekt výsledku místo výjimek pro snazší řešení chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="80ffa-150">You can do this by returning a result object instead exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="80ffa-151">Pomocí pole ověřování s anotacemi dat, například nereplikujete ověření definice.</span><span class="sxs-lookup"><span data-stu-id="80ffa-151">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="80ffa-152">Provádění, ale může být na straně serveru a klienta v případě DTO (příkazy a modely ViewModels, například).</span><span class="sxs-lookup"><span data-stu-id="80ffa-152">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="80ffa-153">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="80ffa-153">Additional resources</span></span>

- <span data-ttu-id="80ffa-154">**Rachel Appel. Úvod k ověření modelu v ASP.NET Core MVC** \\</span><span class="sxs-lookup"><span data-stu-id="80ffa-154">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC** \\</span></span>
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- <span data-ttu-id="80ffa-155">**Rick Anderson. Přidání ověřování** \\</span><span class="sxs-lookup"><span data-stu-id="80ffa-155">**Rick Anderson. Adding validation** \\</span></span>
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- <span data-ttu-id="80ffa-156">**Martina Fowlera. Nahrazení vyvolávání výjimek s oznámením v ověření** \\</span><span class="sxs-lookup"><span data-stu-id="80ffa-156">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations** \\</span></span>
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- <span data-ttu-id="80ffa-157">**Specifikace a vzory oznámení** \\</span><span class="sxs-lookup"><span data-stu-id="80ffa-157">**Specification and Notification Patterns** \\</span></span>
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- <span data-ttu-id="80ffa-158">**Lev Gorodinski. Ověřování v návrhu řízeného doménou (DDD)** \\</span><span class="sxs-lookup"><span data-stu-id="80ffa-158">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)** \\</span></span>
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- <span data-ttu-id="80ffa-159">**Colin konektoru. Ověření modelu domény** \\</span><span class="sxs-lookup"><span data-stu-id="80ffa-159">**Colin Jack. Domain Model Validation** \\</span></span>
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- <span data-ttu-id="80ffa-160">**Jimmy Bogard. Ověření ve světě DDD** \\</span><span class="sxs-lookup"><span data-stu-id="80ffa-160">**Jimmy Bogard. Validation in a DDD world** \\</span></span>
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> <span data-ttu-id="80ffa-161">[Předchozí](enumeration-classes-over-enum-types.md)
> [další](client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="80ffa-161">[Previous](enumeration-classes-over-enum-types.md)
[Next](client-side-validation.md)</span></span>

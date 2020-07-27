---
title: Návrh ověřování ve vrstvě doménového modelu
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Princip klíčových konceptů ověřování modelů domén
ms.date: 10/08/2018
ms.openlocfilehash: f1e2d7430c642ad47f79cdd34d3a65e2cc70e239
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164272"
---
# <a name="design-validations-in-the-domain-model-layer"></a><span data-ttu-id="59ff9-103">Ověřování návrhu ve vrstvě doménového modelu</span><span class="sxs-lookup"><span data-stu-id="59ff9-103">Design validations in the domain model layer</span></span>

<span data-ttu-id="59ff9-104">V DDD lze ověřovací pravidla představit jako invariantní.</span><span class="sxs-lookup"><span data-stu-id="59ff9-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="59ff9-105">Hlavní zodpovědností agregace je vymáhat pro všechny entity v této agregaci invariantní v rámci změny stavu.</span><span class="sxs-lookup"><span data-stu-id="59ff9-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="59ff9-106">Entity domény by měly být vždy platné entity.</span><span class="sxs-lookup"><span data-stu-id="59ff9-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="59ff9-107">Existuje určitý počet invariant pro objekt, který by měl vždy true.</span><span class="sxs-lookup"><span data-stu-id="59ff9-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="59ff9-108">Například objekt položky objednávky má vždy množství, které musí být kladné celé číslo a název článku a cenu.</span><span class="sxs-lookup"><span data-stu-id="59ff9-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="59ff9-109">Proto vynucujeme invariantní je zodpovědností za entity domény (hlavně z agregačního kořene) a objekt entity by neměl být schopný existovat, aniž by byla platná.</span><span class="sxs-lookup"><span data-stu-id="59ff9-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="59ff9-110">Invariantní pravidla jsou jednoduše vyjádřena jako kontrakty a výjimky nebo oznámení jsou vyvolány při jejich porušení.</span><span class="sxs-lookup"><span data-stu-id="59ff9-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="59ff9-111">Důvodem je, že k mnoha chybám dochází, protože objekty jsou ve stavu, kdy by nikdy neměly být v.</span><span class="sxs-lookup"><span data-stu-id="59ff9-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="59ff9-112">Tato [Online diskuze](http://codebetter.com/gregyoung/2009/05/22/always-valid/) je dobrým vysvětlením z Greg Younga.</span><span class="sxs-lookup"><span data-stu-id="59ff9-112">This [online discussion](http://codebetter.com/gregyoung/2009/05/22/always-valid/) is a good explanation from Greg Young.</span></span>

<span data-ttu-id="59ff9-113">Pojďme teď navrhnout SendUserCreationEmailService, který vezme v uživatelském profilu... Jak se můžeme racionalizovat, že v této službě není null?</span><span class="sxs-lookup"><span data-stu-id="59ff9-113">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="59ff9-114">Provedeme to znovu?</span><span class="sxs-lookup"><span data-stu-id="59ff9-114">Do we check it again?</span></span> <span data-ttu-id="59ff9-115">Nebo pravděpodobnější... nebotherte se jenom na to, abyste se mohli podívat a "Doufám na to nejlepší" – Doufáme, že si ho někdo obtěžovat před odesláním.</span><span class="sxs-lookup"><span data-stu-id="59ff9-115">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="59ff9-116">Při použití TDD jedna z prvních testů, které bychom měli psát, je třeba, aby při odeslání zákazníka s názvem s hodnotou null, který by měl vyvolat chybu.</span><span class="sxs-lookup"><span data-stu-id="59ff9-116">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="59ff9-117">Ale až začneme psát tyto typy testů znovu a znovu, uvědomujeme si... "Počkejte, pokud nikdy nepovolujeme, aby se název stala null, ale všechny tyto testy".</span><span class="sxs-lookup"><span data-stu-id="59ff9-117">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests".</span></span>

## <a name="implement-validations-in-the-domain-model-layer"></a><span data-ttu-id="59ff9-118">Implementace ověřování ve vrstvě doménového modelu</span><span class="sxs-lookup"><span data-stu-id="59ff9-118">Implement validations in the domain model layer</span></span>

<span data-ttu-id="59ff9-119">Ověření jsou obvykle implementována v konstruktorech doménových entit nebo v metodách, které mohou entitu aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="59ff9-119">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="59ff9-120">Existuje několik způsobů implementace ověření, jako je například ověřování dat a vyvolávání výjimek, pokud se ověření nepovede.</span><span class="sxs-lookup"><span data-stu-id="59ff9-120">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="59ff9-121">K dispozici jsou také pokročilejší vzory, jako je například použití vzorce specifikace pro ověřování, a vzor oznámení, který vrátí kolekci chyb namísto vrácení výjimky pro každé ověření, když k nim dojde.</span><span class="sxs-lookup"><span data-stu-id="59ff9-121">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validate-conditions-and-throw-exceptions"></a><span data-ttu-id="59ff9-122">Ověřit podmínky a vyvolat výjimky</span><span class="sxs-lookup"><span data-stu-id="59ff9-122">Validate conditions and throw exceptions</span></span>

<span data-ttu-id="59ff9-123">Následující příklad kódu ukazuje nejjednodušší přístup k ověřování v entitě domény tím, že vyvolává výjimku.</span><span class="sxs-lookup"><span data-stu-id="59ff9-123">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="59ff9-124">V tabulce odkazy na konci této části uvidíte odkazy na pokročilejší implementace založené na vzorech, které jsme provedli dříve.</span><span class="sxs-lookup"><span data-stu-id="59ff9-124">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="59ff9-125">Lepším příkladem je Ukázat nutnost zajistit, aby se vnitřní stav nezměnil nebo aby se pro ni nastaly všechny mutace.</span><span class="sxs-lookup"><span data-stu-id="59ff9-125">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="59ff9-126">Například následující implementace by nechala objekt v neplatném stavu:</span><span class="sxs-lookup"><span data-stu-id="59ff9-126">For example, the following implementation would leave the object in an invalid state:</span></span>

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

<span data-ttu-id="59ff9-127">Pokud hodnota stavu není platná, první adresní řádek a město již byly změněny.</span><span class="sxs-lookup"><span data-stu-id="59ff9-127">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="59ff9-128">To může mít neplatnou adresu.</span><span class="sxs-lookup"><span data-stu-id="59ff9-128">That might make the address invalid.</span></span>

<span data-ttu-id="59ff9-129">Podobný přístup lze použít v konstruktoru entity, vyvolává výjimku, aby se zajistilo, že entita je po vytvoření platná.</span><span class="sxs-lookup"><span data-stu-id="59ff9-129">A similar approach can be used in the entity's constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="59ff9-130">Použití atributů ověřování v modelu na základě datových poznámek</span><span class="sxs-lookup"><span data-stu-id="59ff9-130">Use validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="59ff9-131">Poznámky k datům, jako jsou povinné nebo MaxLength atributy, lze použít ke konfiguraci EF Core vlastností pole databáze, jak je vysvětleno podrobněji v sekci [mapování tabulky](infrastructure-persistence-layer-implementation-entity-framework-core.md#table-mapping) , ale [již nefungují pro ověřování entit v EF Core](https://github.com/dotnet/efcore/issues/3680) (ani tato <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> Metoda), protože od EF 4. x v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59ff9-131">Data annotations, like the Required or MaxLength attributes, can be used to configure EF Core database field properties, as explained in detail in the [Table mapping](infrastructure-persistence-layer-implementation-entity-framework-core.md#table-mapping) section, but [they no longer work for entity validation in EF Core](https://github.com/dotnet/efcore/issues/3680) (neither does the <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> method), as they have done since EF 4.x in .NET Framework.</span></span>

<span data-ttu-id="59ff9-132">Poznámky k datům a <xref:System.ComponentModel.DataAnnotations.IValidatableObject> rozhraní lze i nadále použít k ověřování modelu během vytváření modelů, před tím, než se akce kontroleru vystaví jako obvykle, ale tento model má být ViewModel nebo DTO, což je MVC nebo rozhraní API, které se netýká doménového modelu.</span><span class="sxs-lookup"><span data-stu-id="59ff9-132">Data annotations and the <xref:System.ComponentModel.DataAnnotations.IValidatableObject> interface can still be used for model validation during model binding, prior to the controller's actions invocation as usual, but that model is meant to be a ViewModel or DTO and that's an MVC or API concern not a domain model concern.</span></span>

<span data-ttu-id="59ff9-133">V případě, že se v koncepčním rozdílu vyjasní, můžete i nadále používat datové poznámky a `IValidatableObject` v třídě entit pro ověřování, pokud vaše akce obdrží parametr objektu třídy entity, což se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="59ff9-133">Having made the conceptual difference clear, you can still use data annotations and `IValidatableObject` in the entity class for validation, if your actions receive an entity class object parameter, which is not recommended.</span></span> <span data-ttu-id="59ff9-134">V takovém případě se k ověření dojde při vytváření vazby, těsně před vyvoláním akce a můžete zaškrtnout vlastnost ModelState. IsValid kontroleru a ověřit výsledek, ale pak se znovu stane na řadiči, nikoli před trvalým nastavením objektu entity v DbContext, protože to bylo provedeno od verze EF 4. x.</span><span class="sxs-lookup"><span data-stu-id="59ff9-134">In that case, validation will occur upon model binding, just before invoking the action and you can check the controller's ModelState.IsValid property to check the result, but then again, it happens in the controller, not before persisting the entity object in the DbContext, as it had done since EF 4.x.</span></span>

<span data-ttu-id="59ff9-135">Můžete přesto implementovat vlastní ověřování v třídě entity pomocí datových poznámek a `IValidatableObject.Validate` metody přepsáním metody SaveChanges DbContext.</span><span class="sxs-lookup"><span data-stu-id="59ff9-135">You can still implement custom validation in the entity class using data annotations and the `IValidatableObject.Validate` method, by overriding the DbContext's SaveChanges method.</span></span>

<span data-ttu-id="59ff9-136">Můžete si prohlédnout ukázkovou implementaci pro ověřování `IValidatableObject` entit v [tomto komentáři na GitHubu](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539).</span><span class="sxs-lookup"><span data-stu-id="59ff9-136">You can see a sample implementation for validating `IValidatableObject` entities in [this comment on GitHub](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539).</span></span> <span data-ttu-id="59ff9-137">Tato ukázka neprovádí ověřování na základě atributů, ale měla by být snadno implementovaná pomocí reflexe ve stejném přepsání.</span><span class="sxs-lookup"><span data-stu-id="59ff9-137">That sample doesn't do attribute-based validations, but they should be easy to implement using reflection in the same override.</span></span>

<span data-ttu-id="59ff9-138">Z bodu DDD se však model domény nejlépe udržuje s využitím výjimek v metodách chování vaší entity nebo implementací specifikací a vzorců oznámení k vynucujení ověřovacích pravidel.</span><span class="sxs-lookup"><span data-stu-id="59ff9-138">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity's behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span>

<span data-ttu-id="59ff9-139">Může být vhodné použít datové poznámky na vrstvě aplikace v třídách ViewModel (namísto doménových entit), které budou přijímat vstupy, aby bylo možné ověřování modelu v rámci vrstvy uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="59ff9-139">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="59ff9-140">Nicméně to by nemělo být provedeno na základě vyloučení ověřování v rámci doménového modelu.</span><span class="sxs-lookup"><span data-stu-id="59ff9-140">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="59ff9-141">Ověření entit implementací vzoru specifikace a způsobu oznámení</span><span class="sxs-lookup"><span data-stu-id="59ff9-141">Validate entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="59ff9-142">Nakonec složitější přístup k implementaci ověřování v doménovém modelu je implementace vzoru specifikace ve spojení se vzorem oznámení, jak je vysvětleno v některých dalších prostředcích, které jsou uvedeny později.</span><span class="sxs-lookup"><span data-stu-id="59ff9-142">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="59ff9-143">Je třeba uvést, že můžete také použít pouze jeden z těchto vzorů, například ověření ručně pomocí řídicích příkazů, ale použití vzorce oznámení pro skládání a vrácení seznamu chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="59ff9-143">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="use-deferred-validation-in-the-domain"></a><span data-ttu-id="59ff9-144">Použít odložené ověřování v doméně</span><span class="sxs-lookup"><span data-stu-id="59ff9-144">Use deferred validation in the domain</span></span>

<span data-ttu-id="59ff9-145">Existují různé přístupy k odložení platných ověření v doméně.</span><span class="sxs-lookup"><span data-stu-id="59ff9-145">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="59ff9-146">V rámci své knihy [Implementace návrhu založeného na doméně](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)Vaughn Vernon tyto informace v části věnované ověřování.</span><span class="sxs-lookup"><span data-stu-id="59ff9-146">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="59ff9-147">Dvoustupňové ověřování</span><span class="sxs-lookup"><span data-stu-id="59ff9-147">Two-step validation</span></span>

<span data-ttu-id="59ff9-148">Zvažte také dvoustupňové ověřování.</span><span class="sxs-lookup"><span data-stu-id="59ff9-148">Also consider two-step validation.</span></span> <span data-ttu-id="59ff9-149">Použijte ověřování na úrovni polí pro příkazy Přenos dat objekty (DTO) a ověřování na úrovni domény uvnitř svých entit.</span><span class="sxs-lookup"><span data-stu-id="59ff9-149">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="59ff9-150">To lze provést vrácením objektu výsledků namísto výjimek, aby bylo snazší řešit chyby ověřování.</span><span class="sxs-lookup"><span data-stu-id="59ff9-150">You can do this by returning a result object instead of exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="59ff9-151">Při ověřování pomocí datových poznámek například neduplikujete definici ověřování.</span><span class="sxs-lookup"><span data-stu-id="59ff9-151">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="59ff9-152">Spuštění, ale může být na straně serveru i na straně klienta v případě DTO (příkazy a ViewModels).</span><span class="sxs-lookup"><span data-stu-id="59ff9-152">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="59ff9-153">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="59ff9-153">Additional resources</span></span>

- <span data-ttu-id="59ff9-154">**Rachel Appel. Seznámení s ověřováním modelu ve ASP.NET Core MVC** </span><span class="sxs-lookup"><span data-stu-id="59ff9-154">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC** </span></span>\
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- <span data-ttu-id="59ff9-155">**Rick Anderson. Přidání ověřování** </span><span class="sxs-lookup"><span data-stu-id="59ff9-155">**Rick Anderson. Adding validation** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- <span data-ttu-id="59ff9-156">**Martin Fowlera. Nahrazení výjimek při vygenerování oznámení v ověřováních** </span><span class="sxs-lookup"><span data-stu-id="59ff9-156">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations** </span></span>\
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- <span data-ttu-id="59ff9-157">**Specifikace a vzory oznámení** </span><span class="sxs-lookup"><span data-stu-id="59ff9-157">**Specification and Notification Patterns** </span></span>\
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- <span data-ttu-id="59ff9-158">**Lev Gorodinski. Ověřování v návrhu založeném na doméně (DDD)** </span><span class="sxs-lookup"><span data-stu-id="59ff9-158">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)** </span></span>\
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- <span data-ttu-id="59ff9-159">**Konektor Colin. Ověřování doménového modelu** </span><span class="sxs-lookup"><span data-stu-id="59ff9-159">**Colin Jack. Domain Model Validation** </span></span>\
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- <span data-ttu-id="59ff9-160">**Jimmy Bogard. Ověření v DDD World** </span><span class="sxs-lookup"><span data-stu-id="59ff9-160">**Jimmy Bogard. Validation in a DDD world** </span></span>\
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> <span data-ttu-id="59ff9-161">[Předchozí](enumeration-classes-over-enum-types.md) 
>  [Další](client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="59ff9-161">[Previous](enumeration-classes-over-enum-types.md)
[Next](client-side-validation.md)</span></span>

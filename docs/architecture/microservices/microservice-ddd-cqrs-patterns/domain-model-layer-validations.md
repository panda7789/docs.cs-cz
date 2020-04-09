---
title: Návrh ověřování ve vrstvě doménového modelu
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Pochopit klíčové pojmy ověření modelu domény.
ms.date: 10/08/2018
ms.openlocfilehash: d2efc5f3b3267c4573409952791c6e883a01aae2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988502"
---
# <a name="design-validations-in-the-domain-model-layer"></a><span data-ttu-id="162c4-103">Ověření návrhu ve vrstvě modelu domény</span><span class="sxs-lookup"><span data-stu-id="162c4-103">Design validations in the domain model layer</span></span>

<span data-ttu-id="162c4-104">V DDD ověřovací pravidla lze považovat za invariants.</span><span class="sxs-lookup"><span data-stu-id="162c4-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="162c4-105">Hlavní odpovědnost agregace je vynutit invariants napříč změny stavu pro všechny entity v rámci tohoto agregace.</span><span class="sxs-lookup"><span data-stu-id="162c4-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="162c4-106">Entity domény by měly být vždy platnými entitami.</span><span class="sxs-lookup"><span data-stu-id="162c4-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="162c4-107">Existuje určitý počet invariants pro objekt, který by měl být vždy true.</span><span class="sxs-lookup"><span data-stu-id="162c4-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="162c4-108">Například objekt položky objednávky musí mít vždy množství, které musí být kladné celé číslo, plus název článku a cenu.</span><span class="sxs-lookup"><span data-stu-id="162c4-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="162c4-109">Vynucení invariants je proto odpovědností entit domény (zejména agregovaného kořenového adresáře) a objekt entity by neměl být schopen existovat bez platnosti.</span><span class="sxs-lookup"><span data-stu-id="162c4-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="162c4-110">Invariantní pravidla jsou jednoduše vyjádřena jako smlouvy a výjimky nebo oznámení jsou vyvolány, pokud jsou porušeny.</span><span class="sxs-lookup"><span data-stu-id="162c4-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="162c4-111">Důvodem je, že mnoho chyb dochází, protože objekty jsou ve stavu, ve které by nikdy nebyly v.</span><span class="sxs-lookup"><span data-stu-id="162c4-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="162c4-112">Toto je dobré vysvětlení od Greg Young v [on-line diskusi](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/):</span><span class="sxs-lookup"><span data-stu-id="162c4-112">The following is a good explanation from Greg Young in an [online discussion](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="162c4-113">Navrhněme, že nyní máme SendUserCreationEmailService, který má UserProfile ... Jak můžeme racionalizovat v této službě, že název není null?</span><span class="sxs-lookup"><span data-stu-id="162c4-113">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="162c4-114">Podíváme se na to znovu?</span><span class="sxs-lookup"><span data-stu-id="162c4-114">Do we check it again?</span></span> <span data-ttu-id="162c4-115">Nebo spíše ... prostě se neobtěžujete zkontrolovat a "doufat v to nejlepší" - doufáte, že se někdo obtěžoval ověřit, než vám to pošle.</span><span class="sxs-lookup"><span data-stu-id="162c4-115">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="162c4-116">Samozřejmě, pomocí TDD jeden z prvních testů bychom měli psát, je, že když pošlu zákazníka s nulovým názvem, že by měla vyvolat chybu.</span><span class="sxs-lookup"><span data-stu-id="162c4-116">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="162c4-117">Ale jakmile začneme psát tyto druhy testů znovu a znovu si uvědomíme ... "Počkejte, jestli jsme nikdy nedovolili, aby se jméno stalo nulovým, neměli bychom všechny tyto testy"</span><span class="sxs-lookup"><span data-stu-id="162c4-117">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implement-validations-in-the-domain-model-layer"></a><span data-ttu-id="162c4-118">Implementace ověření ve vrstvě modelu domény</span><span class="sxs-lookup"><span data-stu-id="162c4-118">Implement validations in the domain model layer</span></span>

<span data-ttu-id="162c4-119">Ověření jsou obvykle implementována v konstruktorech entit domény nebo v metodách, které mohou entitu aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="162c4-119">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="162c4-120">Existuje několik způsobů, jak implementovat ověření, jako je například ověření dat a vyvolání výjimek, pokud se ověření nezdaří.</span><span class="sxs-lookup"><span data-stu-id="162c4-120">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="162c4-121">Existují také pokročilejší vzory, jako je například použití specifikace vzor pro ověření a vzor oznámení vrátit kolekci chyb namísto vrácení výjimky pro každé ověření, jak k němu dojde.</span><span class="sxs-lookup"><span data-stu-id="162c4-121">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validate-conditions-and-throw-exceptions"></a><span data-ttu-id="162c4-122">Ověřit podmínky a vyvolat výjimky</span><span class="sxs-lookup"><span data-stu-id="162c4-122">Validate conditions and throw exceptions</span></span>

<span data-ttu-id="162c4-123">Následující příklad kódu ukazuje nejjednodušší přístup k ověření v entitě domény vyvoláním výjimky.</span><span class="sxs-lookup"><span data-stu-id="162c4-123">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="162c4-124">V tabulce odkazů na konci této části můžete zobrazit odkazy na pokročilejší implementace na základě vzorů, které jsme diskutovali dříve.</span><span class="sxs-lookup"><span data-stu-id="162c4-124">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="162c4-125">Lepší příklad by demonstroval potřebu zajistit, aby se vnitřní stav nezměnil nebo že došlo ke všem mutacím pro metodu.</span><span class="sxs-lookup"><span data-stu-id="162c4-125">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="162c4-126">Například následující implementace by ponechat objekt v neplatném stavu:</span><span class="sxs-lookup"><span data-stu-id="162c4-126">For example, the following implementation would leave the object in an invalid state:</span></span>

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

<span data-ttu-id="162c4-127">Pokud je hodnota státu neplatná, první řádek adresy a město již byly změněny.</span><span class="sxs-lookup"><span data-stu-id="162c4-127">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="162c4-128">To by mohlo způsobit neplatnost adresy.</span><span class="sxs-lookup"><span data-stu-id="162c4-128">That might make the address invalid.</span></span>

<span data-ttu-id="162c4-129">Podobný přístup lze použít v konstruktoru entity, vyvolání výjimku a ujistěte se, že entita je platná, jakmile je vytvořena.</span><span class="sxs-lookup"><span data-stu-id="162c4-129">A similar approach can be used in the entity's constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="162c4-130">Použití ověřovacích atributů v modelu na základě datových poznámk</span><span class="sxs-lookup"><span data-stu-id="162c4-130">Use validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="162c4-131">Datové poznámky, jako jsou atributy Povinné nebo MaxLength, lze použít ke konfiguraci vlastností pole EF Core databáze, jak je podrobně vysvětleno v části [Mapování tabulky,](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) ale [již nefungují pro ověření entity v EF Core](https://github.com/dotnet/efcore/issues/3680) (ani <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> metoda), jak tomu bylo od EF 4.x v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="162c4-131">Data annotations, like the Required or MaxLength attributes, can be used to configure EF Core database field properties, as explained in detail in the [Table mapping](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) section, but [they no longer work for entity validation in EF Core](https://github.com/dotnet/efcore/issues/3680) (neither does the <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> method), as they have done since EF 4.x in .NET Framework.</span></span>

<span data-ttu-id="162c4-132">Data anotace <xref:System.ComponentModel.DataAnnotations.IValidatableObject> a rozhraní lze stále použít pro ověření modelu během vazby modelu, před vyvolání akce řadiče jako obvykle, ale tento model má být ViewModel nebo DTO a to je MVC nebo ROZHRANÍ rozhraní se týká není problém modelu domény.</span><span class="sxs-lookup"><span data-stu-id="162c4-132">Data annotations and the <xref:System.ComponentModel.DataAnnotations.IValidatableObject> interface can still be used for model validation during model binding, prior to the controller's actions invocation as usual, but that model is meant to be a ViewModel or DTO and that's an MVC or API concern not a domain model concern.</span></span>

<span data-ttu-id="162c4-133">Po odstranění koncepčního rozdílu můžete stále používat datové `IValidatableObject` poznámky a ve třídě entity pro ověření, pokud vaše akce obdrží parametr objektu třídy entity, což se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="162c4-133">Having made the conceptual difference clear, you can still use data annotations and `IValidatableObject` in the entity class for validation, if your actions receive an entity class object parameter, which is not recommended.</span></span> <span data-ttu-id="162c4-134">V takovém případě dojde k ověření při vazby modelu, těsně před vyvolání akce a můžete zkontrolovat řadič modelState.IsValid vlastnost zkontrolovat výsledek, ale pak znovu se to stane v řadiči, ne před uchování objektu entity v DbContext, jako tomu bylo od EF 4.x.</span><span class="sxs-lookup"><span data-stu-id="162c4-134">In that case, validation will occur upon model binding, just before invoking the action and you can check the controller's ModelState.IsValid property to check the result, but then again, it happens in the controller, not before persisting the entity object in the DbContext, as it had done since EF 4.x.</span></span>

<span data-ttu-id="162c4-135">Stále můžete implementovat vlastní ověření ve třídě entity pomocí `IValidatableObject.Validate` datových anotací a metody přepsáním metody SaveChanges společnosti DbContext.</span><span class="sxs-lookup"><span data-stu-id="162c4-135">You can still implement custom validation in the entity class using data annotations and the `IValidatableObject.Validate` method, by overriding the DbContext's SaveChanges method.</span></span>

<span data-ttu-id="162c4-136">Ukázkovou implementaci pro ověřování `IValidatableObject` entit můžete zobrazit v tomto [komentáři na GitHubu](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539).</span><span class="sxs-lookup"><span data-stu-id="162c4-136">You can see a sample implementation for validating `IValidatableObject` entities in [this comment on GitHub](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539).</span></span> <span data-ttu-id="162c4-137">Tento vzorek neprovádí ověřování na základě atributů, ale měly by být snadno implementovat pomocí reflexe ve stejném přepsání.</span><span class="sxs-lookup"><span data-stu-id="162c4-137">That sample doesn't do attribute-based validations, but they should be easy to implement using reflection in the same override.</span></span>

<span data-ttu-id="162c4-138">Z hlediska DDD je však model domény nejlépe udržován štíhlý s použitím výjimek v metodách chování entity nebo implementací vzorů specifikace a oznámení k vynucení ověřovacích pravidel.</span><span class="sxs-lookup"><span data-stu-id="162c4-138">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity's behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span>

<span data-ttu-id="162c4-139">Může mít smysl používat datové poznámky na aplikační vrstvě ve třídách ViewModel (namísto entit domény), které budou přijímat vstup, aby bylo možné ověřit ověření modelu v rámci vrstvy ui.</span><span class="sxs-lookup"><span data-stu-id="162c4-139">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="162c4-140">To by však nemělo být provedeno při vyloučení ověření v rámci modelu domény.</span><span class="sxs-lookup"><span data-stu-id="162c4-140">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="162c4-141">Ověření entit implementací vzoru specifikace a vzoru oznámení</span><span class="sxs-lookup"><span data-stu-id="162c4-141">Validate entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="162c4-142">Nakonec propracovanější přístup k implementaci ověření v modelu domény je implementací specifikace vzor ve spojení se vzorem oznámení, jak je vysvětleno v některých dalších prostředků uvedených později.</span><span class="sxs-lookup"><span data-stu-id="162c4-142">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="162c4-143">Stojí za zmínku, že můžete také použít pouze jeden z těchto vzorů – například ověření ručně s příkazy ovládacího prvku, ale pomocí vzoru oznámení zásobníku a vrátit seznam chyb ověření.</span><span class="sxs-lookup"><span data-stu-id="162c4-143">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="use-deferred-validation-in-the-domain"></a><span data-ttu-id="162c4-144">Použít odložené ověření v doméně</span><span class="sxs-lookup"><span data-stu-id="162c4-144">Use deferred validation in the domain</span></span>

<span data-ttu-id="162c4-145">Existují různé přístupy k řešení odložené ověření v doméně.</span><span class="sxs-lookup"><span data-stu-id="162c4-145">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="162c4-146">Ve své [knize Implementace Domény-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon diskutuje tyto v sekci o validaci.</span><span class="sxs-lookup"><span data-stu-id="162c4-146">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="162c4-147">Dvoustupňové ověření</span><span class="sxs-lookup"><span data-stu-id="162c4-147">Two-step validation</span></span>

<span data-ttu-id="162c4-148">Zvažte také dvoustupňové ověření.</span><span class="sxs-lookup"><span data-stu-id="162c4-148">Also consider two-step validation.</span></span> <span data-ttu-id="162c4-149">Použijte ověření na úrovni pole u příkazů Objekty přenosu dat (DTO) a ověření na úrovni domény uvnitř entit.</span><span class="sxs-lookup"><span data-stu-id="162c4-149">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="162c4-150">Můžete to provést vrácením objektu result namísto výjimek, aby bylo snazší řešit chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="162c4-150">You can do this by returning a result object instead of exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="162c4-151">Pomocí ověření pole s anotacemi dat například neduplikujete definici ověření.</span><span class="sxs-lookup"><span data-stu-id="162c4-151">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="162c4-152">Spuštění však může být na straně serveru i na straně klienta v případě DTO (příkazy a ViewModels, například).</span><span class="sxs-lookup"><span data-stu-id="162c4-152">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="162c4-153">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="162c4-153">Additional resources</span></span>

- <span data-ttu-id="162c4-154">**Rachel Anetelová. Úvod do validace modelu v ASP.NET Core MVC** </span><span class="sxs-lookup"><span data-stu-id="162c4-154">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC** </span></span>\
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- <span data-ttu-id="162c4-155">**Rick Anderson. Přidání ověření** </span><span class="sxs-lookup"><span data-stu-id="162c4-155">**Rick Anderson. Adding validation** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- <span data-ttu-id="162c4-156">**Martin Fowler. Nahrazení výtečů výjimky oznámení v ověření** </span><span class="sxs-lookup"><span data-stu-id="162c4-156">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations** </span></span>\
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- <span data-ttu-id="162c4-157">**Specifikace a vzory oznámení** </span><span class="sxs-lookup"><span data-stu-id="162c4-157">**Specification and Notification Patterns** </span></span>\
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- <span data-ttu-id="162c4-158">**Lev Gorodinski. Ověření v návrhu řízeném doménou (DDD)** </span><span class="sxs-lookup"><span data-stu-id="162c4-158">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)** </span></span>\
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- <span data-ttu-id="162c4-159">**Colin jack, to je ono. Ověření modelu domény** </span><span class="sxs-lookup"><span data-stu-id="162c4-159">**Colin Jack. Domain Model Validation** </span></span>\
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- <span data-ttu-id="162c4-160">**Jimmyho Bogarda. Validace ve světě DDD** </span><span class="sxs-lookup"><span data-stu-id="162c4-160">**Jimmy Bogard. Validation in a DDD world** </span></span>\
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> <span data-ttu-id="162c4-161">[Předchozí](enumeration-classes-over-enum-types.md)
> [další](client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="162c4-161">[Previous](enumeration-classes-over-enum-types.md)
[Next](client-side-validation.md)</span></span>

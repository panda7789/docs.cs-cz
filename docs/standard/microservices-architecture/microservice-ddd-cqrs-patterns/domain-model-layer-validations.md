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
# <a name="designing-validations-in-the-domain-model-layer"></a>Návrh ověřování ve vrstvě doménového modelu

V DDD ověřovacích pravidel si lze představit jako výstupních podmínek. Hlavní zodpovědností agregace je vynucovat změny stavu pro všechny entity v rámci této agregaci výstupních podmínek.

Domény entity musí být vždy platný entity. Existuje je určitý počet výstupních podmínek pro objekt, který by měl mít hodnotu true. Například objekt pořadí položek má vždy mít množství, které musí být kladné celé číslo a název článku a ceny. Proto zodpovídá za vynucování výstupních podmínek entit domény (zejména z agregační root) a objekt entity by neměla být schopná existovat bez platné. Výchozí pravidla se jednoduše vyjádřený jako smluv a výjimky nebo oznámení jsou vyvolány, když je porušena.

Zdůvodnění to je, že mnoho chyb dojít, protože objekty jsou ve stavu, který by měl mít nikdy nebyla v. Tady je dobrý popis z Grega Younga: v [diskuse](https://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):

Navrhnout Řekněme, že nyní máme SendUserCreationEmailService, která přebírá... UserProfile jak můžete jsme racionalizovat dané služby, název není null? Zkontrolujeme ho znovu? Nebo vyšší pravděpodobnost... je právě není Nepokoušejte se ke kontrole a "doufat těch nejlepších" – Doufáme, že někdo bothered abyste ověřili, že před odesláním. Samozřejmě použití vývoje Řízeného, jeden první testů, které jsme se zápis, je, že pokud poslat zákazníkovi s názvem hodnotu null, že by měla vyvolat chybu. Ale když jsme začali psát tyto druhy testů tytéž Uvědomujeme... "Počkejte, pokud jsme název se může nikdy null by máme všechny tyto testy"

## <a name="implementing-validations-in-the-domain-model-layer"></a>Implementace ověření ve vrstvě doménového modelu

Ověření jsou obvykle implementovány v konstruktorech entita domény nebo v metodách, které můžete aktualizovat entitu. Existuje několik způsobů, jak implementovat ověřování, jako je například ověřování dat a vyvolání výjimky, pokud se ověření nezdaří. Existují také pokročilejší vzory, třeba pomocí vzoru specifikace pro ověření a vzor oznámení k vrácení kolekce chyb místo vrácení výjimky pro každé ověření, protože k ní dojde.

### <a name="validating-conditions-and-throwing-exceptions"></a>Ověření podmínek a vyvolávání výjimek

Následující příklad kódu ukazuje nejjednodušším přístupem k ověření v entita domény vyvoláním výjimky. V tabulce odkazy na konci této části se zobrazí odkazy na pokročilejší implementací na základě vzorců, které mají jsme probírali dříve.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Lepší příkladu by ukazují, je potřeba zajistit, že se nezměnil vnitřní stav, nebo že došlo k všechny mutace pro metodu. Například následující implementaci zůstane objekt v neplatném stavu:

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

Pokud je neplatná hodnota stavu, první řádek adresy a Město již byly změněny. Adresa pro, který může být neplatný.

Podobný přístup je možné v konstruktoru entity, vyvolá výjimku, abyste měli jistotu, že entita je platný po jeho vytvoření.

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a>Pomocí atributů ověření v modelu, podle datových poznámek

Další možností je použití atributů ověření založené na datových poznámek. Ověření atributy poskytují způsob, jak konfigurovat ověření modelu, které se koncepčně podobá ověření na pole v databázové tabulky. To zahrnuje omezení, jako je například přiřazení datových typů nebo povinná pole. Jiné typy ověření, které zahrnuje použití vzorců k datům a vynucování obchodních pravidel, jako je číslo platební karty, telefonní číslo nebo e-mailovou adresu. Ověřování atributů usnadňují vynucují požadavky.

Ale jak je znázorněno v následujícím kódu, tento přístup může být příliš nežádoucí v modelu DDD, protože to je závislá na ModelState.IsValid z Microsoft.AspNetCore.Mvc.ModelState, které je nutné volat z vašeho řadiče MVC. Ověření modelu nastává před každou volaná akce kontroleru a zodpovídá za metoda kontroleru ke kontrole výsledku volání ModelState.IsValid a reagují odpovídajícím způsobem. Závisí na tom, rozhodnout a použít ho úzce párované chcete modelu, který má být s tuto infrastrukturu.

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

Nicméně z DDD hlediska, doménový model nejlépe, zůstane lean se použití výjimek v metodách chování vaší entity, nebo prostřednictvím implementace vzorů specifikaci a oznámení k vynucení pravidel ověřování. Ověření architektury, jako jsou datové poznámky v ASP.NET Core nebo jakékoli jiné ověření architektur, jako třeba FluentValidation provádění požadavku k vyvolání aplikační platformu. Například při volání metody ModelState.IsValid anotacemi dat, budete muset vyvolat kontrolery ASP.NET.

Může být vhodné k použití anotací dat v aplikační vrstvě v tříd ViewModel (namísto domény entity), které bude přijímat vstup, aby se ověření modelu ve vrstvě uživatelského rozhraní. Ale to by neměl být provedeno v vyloučení ověřování v rámci modelu domény.

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Ověřování entity díky implementaci vzoru specifikaci a vzor oznámení

Nakonec komplikovanějších přístupem k implementaci ověření v doménovém modelu je implementace vzoru specifikace ve spojení se vzorem oznámení, jak je vysvětleno v některé z dalších prostředků najdete dál.

Stojí za zmínku, že můžete použít také pouze jedna z těchto vzorců – například ověřování ručně řídicí příkazy, ale pomocí vzoru oznámení do zásobníku a vrátí seznam chyb při ověřování.

### <a name="using-deferred-validation-in-the-domain"></a>Použití odložené ověřování v doméně

Existují různé přístupy k řešení odložené ověření v doméně. Ve své knize [Implementing Domain-Driven návrhu](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon probírají v části v ověřování.

### <a name="two-step-validation"></a>Dvoustupňové ověřování

Zvažte také dvoustupňové ověření. V příkazu objekty přenosu dat (DTO) a ověřování na úrovni domény uvnitř vaší entity pomocí ověření na úrovni pole. Můžete to provést tak, že vrací objekt výsledku místo výjimek pro snazší řešení chyb ověřování.

Pomocí pole ověřování s anotacemi dat, například nereplikujete ověření definice. Provádění, ale může být na straně serveru a klienta v případě DTO (příkazy a modely ViewModels, například).

## <a name="additional-resources"></a>Další zdroje

-   **Rachel Appel. Úvod k ověření modelu v ASP.NET Core MVC**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

-   **Rick Anderson. Přidání ověřování**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

-   **Martina Fowlera. Nahrazení vyvolávání výjimek s oznámením v ověření**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

-   **Specifikace a vzory oznámení**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

-   **Lev Gorodinski. Ověřování v návrhu řízeného doménou (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

-   **Colin konektoru. Ověření modelu domény**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)

-   **Jimmy Bogard. Ověření ve světě DDD**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)


>[!div class="step-by-step"]
[Předchozí](enumeration-classes-over-enum-types.md)
[další](client-side-validation.md)

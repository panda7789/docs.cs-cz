---
title: Navrhování ověření ve vrstvě modelu domény.
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Navrhování ověření ve vrstvě modelu domény.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ce3cb0c79cbd492224ce1d4ecb25cd02062f11cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578947"
---
# <a name="designing-validations-in-the-domain-model-layer"></a>Navrhování ověření ve vrstvě modelu domény.

V DDD může být ověřovacích pravidel představit jako výstupních podmínek. Hlavní zodpovědností agregace je vynutit výstupních podmínek napříč změny stavu pro všechny entity v rámci této agregace.

Entity domény by mělo být vždy platný entity. Existují počet výstupních podmínek pro objekt, který by měl mít vždy hodnotu true. Například objekt pořadí položek vždy musí mít množství, které musí být kladné celé číslo a název článku a cena. Proto výstupních podmínek vynucení má na starosti entit domény (zejména o agregační root) a objekt entity neměli mít možnost existovat, aniž by musel být platný. Výchozí pravidla se jednoduše vyjádřený jako kontrakty a výjimky nebo oznámení se vyvolá, když se porušení.

Zdůvodnění to je, že mnoho chyb dojít, protože jsou objekty ve stavu, který by měl mít nikdy nebyla v. Toto je dobré vysvětlení z Gregu Young v [online diskusní](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):

Umožňuje navrhnout, že máme teď SendUserCreationEmailService, která přijímá UserProfile... jak můžete jsme zefektivní v této službě, že název není null? Jsme ji znovu zkontrolujte? Nebo vyšší pravděpodobnost... právě se nemáte Nepokoušejte se zkontrolovat a "Naděje pro nejlepší" – naděje někdo bothered k ověření před odesláním pro vás. Samozřejmě použití vývoje řízeného Testováním jeden první testů, které jsme být zápis, je, že pokud poslat zákazníkovi s hodnotou null názvem, aby měli vyvolá chybu. Ale po jsme začali psát tyto druhy testy opakovaně jsme zjistili... "Počkejte Pokud jsme nikdy název stane null jsme nemohli mají všechny tyto testy"

## <a name="implementing-validations-in-the-domain-model-layer"></a>Implementace ověření ve vrstvě modelu domény.

Ověření se většinou implementují v konstruktorech entita domény nebo metody, které lze aktualizaci entity. K implementaci ověření, například ověřování dat a aktivaci výjimky, pokud se ověření nezdaří několika způsoby. Existují také pokročilejší vzory, třeba pomocí vzoru specifikace pro ověření a v oznámení vzoru má vracet kolekci chyby místo vrací výjimku pro každé ověření, protože k ní dojde.

### <a name="validating-conditions-and-throwing-exceptions"></a>Ověřování podmínky a vyvolávání výjimek

Následující příklad kódu zobrazuje nejjednodušším přístupem při ověřování v entita domény podle vyvolání k výjimce. V tabulce odkazy na konci této části zobrazíte odkazy na pokročilejší implementace podle vzorů, které jsme dříve popsané.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Lepší příkladu by ukazují, je třeba zajistit, že se nezměnila vnitřní stav, nebo že došlo k všechny mutací pro metodu. Například následující implementaci ponecháte objekt v neplatném stavu:

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

Pokud hodnota stavu je neplatná, první řádek adresy a Město již byly změněny. Adresa pro které by mohly způsobit neplatná.

Podobný postup lze použít v konstruktoru entity, vyvolá výjimku, abyste měli jistotu, že tato entita je platný po vytvoření.

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a>Pomocí ověřování atributů v modelu, podle datových poznámek

Další možností je použití atributů ověření podle datových poznámek. Atributy ověření zadejte způsob, jak nakonfigurovat ověření modelu, který se koncepčně podobá ověření na pole v tabulkách databáze. To zahrnuje omezení, jako je například přiřazení datových typů nebo povinná pole. Ostatní typy ověření, které zahrnuje použití vzorce k datům a vynutit obchodních pravidel, jako je číslo platební karty, telefonní číslo nebo e-mailovou adresu. Atributy ověření usnadňují vynucují požadavky.

Ale, jak je znázorněno v následujícím kódu, tento přístup může být příliš rušivý v modelu DDD, protože má závislost na ModelState.IsValid z Microsoft.AspNetCore.Mvc.ModelState, které je třeba volat z řadičů MVC. Ověření modelu proběhne před každou volaná akce kontroleru a metoda kontroleru odpovídá kontrolovat výsledek volání ModelState.IsValid a náležitě reagovat. Rozhodnout a použít ho závisí na tom úzce párované chcete modelu, který má být s tuto infrastrukturu.

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

Však z DDD hlediska, modelu domény je lepší je ponechat štíhlého s použití výjimek v metodách chování vaší entity, nebo implementace vzorů specifikace a oznámení k vynucení pravidel ověřování. Ověření architektury, jako je datových poznámek v ASP.NET Core nebo jiných rozhraní ověření jako FluentValidation provádění požadavku k vyvolání rozhraní. Například při volání metody ModelState.IsValid v datových poznámek, budete muset vyvolání řadiče ASP.NET.

Můžete ho mít smysl použití datové poznámky na aplikační vrstvu v třídách ViewModel (namísto domény entity), která bude přijímat vstup, aby bylo možné ověření modelu v rámci uživatelského rozhraní vrstvy. Ale to neměli dělat na vyloučení ověření v rámci modelu domény.

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Ověřování entity implementací vzoru specifikaci a vzoru oznámení

Nakonec komplikovanějších přístup k ověření, které implementují v modelu domény je implementací vzoru specifikace ve spojení s vzoru oznámení, jak je popsáno v některé další zdroje najdete dál.

Je důležité zmínit, že můžete taky právě jeden z těchto vzory – například ověřování ručně s řídicí příkazy, ale pomocí vzoru oznámení zásobníku a vrátíte se seznamu chyb ověřování.

### <a name="using-deferred-validation-in-the-domain"></a>Pomocí odložené ověřování v doméně

Existují různé přístupy k řešení odložené ověření v doméně. V jeho kniha [Implementing Domain-Driven návrhu](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon popisuje v části na ověření.

### <a name="two-step-validation"></a>Dvoustupňové ověření

Zvažte také dvoustupňové ověření. Použijte ověření na úrovni pole v příkazu objekty přenos dat (DTOs) a na úrovni domény ověření uvnitř vaší entity. Můžete k tomu vrácením výsledný objekt místo výjimky abyste snadněji řešit chyby ověření.

Pomocí pole ověřování s anotacemi dat, například můžete není duplicitní ověření definice. Spuštění, ale může být současně na straně serveru a na straně klienta v případě DTOs (příkazy a ViewModels, například).

## <a name="additional-resources"></a>Další zdroje

-   **Rachel Appel. Úvod k ověření modelu v aplikaci ASP.NET MVC jádra**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

-   **Rick Anderson. Přidání ověřování**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

-   **Martin Fowler. Nahrazení vyvolání výjimky s oznámení v ověření**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

-   **Specifikace a vzory oznámení**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

-   **Lev Gorodinski. Ověřování v doméně řízené návrhu (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

-   **Colin konektoru. Ověření modelu domény**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)

-   **Jimmy Bogard. Ověření DDD světě**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)


>[!div class="step-by-step"]
[Předchozí] (– výčet třídy over výčtu types.md) [Další] (klientské straně validation.md)

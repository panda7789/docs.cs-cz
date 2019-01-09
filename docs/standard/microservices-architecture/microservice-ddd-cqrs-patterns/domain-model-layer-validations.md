---
title: Návrh ověřování ve vrstvě doménového modelu
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Klíčové koncepce ověření modelu domény.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: d48c78e6ea63ea1a2f3dbfea6b9fec646493c751
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148068"
---
# <a name="design-validations-in-the-domain-model-layer"></a>Návrh ověřování ve vrstvě doménového modelu

V DDD ověřovacích pravidel si lze představit jako výstupních podmínek. Hlavní zodpovědností agregace je vynucovat změny stavu pro všechny entity v rámci této agregaci výstupních podmínek.

Domény entity musí být vždy platný entity. Existuje je určitý počet výstupních podmínek pro objekt, který by měl mít hodnotu true. Například objekt pořadí položek má vždy mít množství, které musí být kladné celé číslo a název článku a ceny. Proto zodpovídá za vynucování výstupních podmínek entit domény (zejména z agregační root) a objekt entity by neměla být schopná existovat bez platné. Výchozí pravidla se jednoduše vyjádřený jako smluv a výjimky nebo oznámení jsou vyvolány, když je porušena.

Zdůvodnění to je, že mnoho chyb dojít, protože objekty jsou ve stavu, který by měl mít nikdy nebyla v. Tady je dobrý popis z Grega Younga: v [diskuse](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/):

Navrhnout Řekněme, že nyní máme SendUserCreationEmailService, která přebírá... UserProfile jak můžete jsme racionalizovat dané služby, název není null? Zkontrolujeme ho znovu? Nebo vyšší pravděpodobnost... je právě není Nepokoušejte se ke kontrole a "doufat těch nejlepších" – Doufáme, že někdo bothered abyste ověřili, že před odesláním. Samozřejmě použití vývoje Řízeného, jeden první testů, které jsme se zápis, je, že pokud poslat zákazníkovi s názvem hodnotu null, že by měla vyvolat chybu. Ale když jsme začali psát tyto druhy testů tytéž Uvědomujeme... "Počkejte, pokud jsme název se může nikdy null by máme všechny tyto testy"

## <a name="implement-validations-in-the-domain-model-layer"></a>Implementace ověřování ve vrstvě doménového modelu

Ověření jsou obvykle implementovány v konstruktorech entita domény nebo v metodách, které můžete aktualizovat entitu. Existuje několik způsobů, jak implementovat ověřování, jako je například ověřování dat a vyvolání výjimky, pokud se ověření nezdaří. Existují také pokročilejší vzory, třeba pomocí vzoru specifikace pro ověření a vzor oznámení k vrácení kolekce chyb místo vrácení výjimky pro každé ověření, protože k ní dojde.

### <a name="validate-conditions-and-throw-exceptions"></a>Ověření podmínek a vyvolávat výjimky

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

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a>Použití atributů ověření v modelu na základě dat poznámky

Anotací dat, jako jsou požadované nebo MaxLength atributy lze použít ke konfiguraci vlastností pole databáze EF Core, jak je podrobně popsaný v části [mapování tabulky](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) oddílu, ale [už nebude fungovat pro entitu ověřování v EF Core](https://github.com/aspnet/EntityFrameworkCore/issues/3680) (ani nemá <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> metoda), jak to máte všechno od EF v rozhraní .NET Framework 4.x.

Datové poznámky a <xref:System.ComponentModel.DataAnnotations.IValidatableObject> rozhraní je stále možné k ověření modelu během vazby modelu, před vyvolání akce kontroleru obvyklým způsobem, ale je model určen ViewModel nebo objekt DTO a, který je MVC nebo rozhraní API není doménový model žádný problém.

Po provedení koncepční rozdíly vymazat, můžete dál používat datových poznámek a `IValidatableObject` ve třídě entity pro ověření, pokud vaše akce zobrazí parametr objektu entity třídy, což se nedoporučuje. V takovém případě dojde k ověření při vazby modelu, těsně před vyvolání akce a můžete zkontrolovat vlastnost ModelState.IsValid kontroleru zkontrolujte výsledek, ale pak znovu dojde v kontroleru, ne před uložením objektu entity v Kontext databáze, protože provedli od EF 4.x.

Stále můžete implementovat vlastní ověřování ve třídě entity pomocí datových poznámek a `IValidatableObject.Validate` metodu tak, že přepíšete metodu SaveChanges DbContext.

Zobrazí se ukázková implementace pro ověření `IValidatableObject` entity v [tento komentář na Githubu](https://github.com/aspnet/EntityFrameworkCore/issues/3680#issuecomment-155502539). Ukázky neprovádí ověřování založených na atributech, ale měly by být snadno se implementuje pomocí reflexe ve stejném přepsání.

Nicméně z DDD hlediska, doménový model nejlépe, zůstane lean se použití výjimek v metodách chování vaší entity, nebo prostřednictvím implementace vzorů specifikaci a oznámení k vynucení pravidel ověřování.

Může být vhodné k použití anotací dat v aplikační vrstvě v tříd ViewModel (namísto domény entity), které bude přijímat vstup, aby se ověření modelu ve vrstvě uživatelského rozhraní. Ale to by neměl být provedeno v vyloučení ověřování v rámci modelu domény.

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Ověření entity díky implementaci vzoru specifikaci a vzor oznámení

Nakonec komplikovanějších přístupem k implementaci ověření v doménovém modelu je implementace vzoru specifikace ve spojení se vzorem oznámení, jak je vysvětleno v některé z dalších prostředků najdete dál.

Stojí za zmínku, že můžete použít také pouze jedna z těchto vzorců – například ověřování ručně řídicí příkazy, ale pomocí vzoru oznámení do zásobníku a vrátí seznam chyb při ověřování.

### <a name="use-deferred-validation-in-the-domain"></a>Používají odložené ověřování v doméně

Existují různé přístupy k řešení odložené ověření v doméně. Ve své knize [Implementing Domain-Driven návrhu](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon probírají v části v ověřování.

### <a name="two-step-validation"></a>Dvoustupňové ověřování

Zvažte také dvoustupňové ověření. V příkazu objekty přenosu dat (DTO) a ověřování na úrovni domény uvnitř vaší entity pomocí ověření na úrovni pole. Můžete to provést tak, že vrací objekt výsledku místo výjimek pro snazší řešení chyb ověřování.

Pomocí pole ověřování s anotacemi dat, například nereplikujete ověření definice. Provádění, ale může být na straně serveru a klienta v případě DTO (příkazy a modely ViewModels, například).

## <a name="additional-resources"></a>Další zdroje

- **Rachel Appel. Úvod k ověření modelu v ASP.NET Core MVC** \
  [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

- **Rick Anderson. Přidání ověřování** \
  [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

- **Martina Fowlera. Nahrazení vyvolávání výjimek s oznámením v ověření** \
  [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

- **Specifikace a vzory oznámení** \
  [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

- **Lev Gorodinski. Ověřování v návrhu řízeného doménou (DDD)** \
  [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

- **Colin konektoru. Ověření modelu domény** \
  [*https://colinjack.blogspot.com/2008/03/domain-model-validation.html*](https://colinjack.blogspot.com/2008/03/domain-model-validation.html)

- **Jimmy Bogard. Ověření ve světě DDD** \
  [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)

>[!div class="step-by-step"]
>[Předchozí](enumeration-classes-over-enum-types.md)
>[další](client-side-validation.md)

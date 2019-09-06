---
title: Návrh ověřování ve vrstvě doménového modelu
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Princip klíčových konceptů ověřování modelů domén
ms.date: 10/08/2018
ms.openlocfilehash: 1d3196d2130df33969ed231bccfe0fc6f0af2ad8
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295962"
---
# <a name="design-validations-in-the-domain-model-layer"></a>Ověřování návrhu ve vrstvě doménového modelu

V DDD lze ověřovací pravidla představit jako invariantní. Hlavní zodpovědností agregace je vymáhat pro všechny entity v této agregaci invariantní v rámci změny stavu.

Entity domény by měly být vždy platné entity. Existuje určitý počet invariant pro objekt, který by měl vždy true. Například objekt položky objednávky má vždy množství, které musí být kladné celé číslo a název článku a cenu. Proto vynucujeme invariantní je zodpovědností za entity domény (hlavně z agregačního kořene) a objekt entity by neměl být schopný existovat, aniž by byla platná. Invariantní pravidla jsou jednoduše vyjádřena jako kontrakty a výjimky nebo oznámení jsou vyvolány při jejich porušení.

Důvodem je, že k mnoha chybám dochází, protože objekty jsou ve stavu, kdy by nikdy neměly být v. Následuje dobré vysvětlení z Greg Younga v [online diskuzi](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/):

Pojďme teď navrhnout SendUserCreationEmailService, který vezme v uživatelském profilu... Jak se můžeme racionalizovat, že v této službě není null? Provedeme to znovu? Nebo pravděpodobnější... nebotherte se jenom na to, abyste se mohli podívat a "Doufám na to nejlepší" – Doufáme, že si ho někdo obtěžovat před odesláním. Při použití TDD jedna z prvních testů, které bychom měli psát, je třeba, aby při odeslání zákazníka s názvem s hodnotou null, který by měl vyvolat chybu. Ale až začneme psát tyto typy testů znovu a znovu, uvědomujeme si... "Počkejte, pokud nikdy nepovolujeme, aby se název stala hodnotou null. nedostali jsme všechny tyto testy."

## <a name="implement-validations-in-the-domain-model-layer"></a>Implementace ověřování ve vrstvě doménového modelu

Ověření jsou obvykle implementována v konstruktorech doménových entit nebo v metodách, které mohou entitu aktualizovat. Existuje několik způsobů implementace ověření, jako je například ověřování dat a vyvolávání výjimek, pokud se ověření nepovede. K dispozici jsou také pokročilejší vzory, jako je například použití vzorce specifikace pro ověřování, a vzor oznámení, který vrátí kolekci chyb namísto vrácení výjimky pro každé ověření, když k nim dojde.

### <a name="validate-conditions-and-throw-exceptions"></a>Ověřit podmínky a vyvolat výjimky

Následující příklad kódu ukazuje nejjednodušší přístup k ověřování v entitě domény tím, že vyvolává výjimku. V tabulce odkazy na konci této části uvidíte odkazy na pokročilejší implementace založené na vzorech, které jsme provedli dříve.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Lepším příkladem je Ukázat nutnost zajistit, aby se vnitřní stav nezměnil nebo aby se pro ni nastaly všechny mutace. Například následující implementace by nechala objekt v neplatném stavu:

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

Pokud hodnota stavu není platná, první adresní řádek a město již byly změněny. To může mít neplatnou adresu.

Podobný přístup lze použít v konstruktoru entity, vyvolává výjimku, aby se zajistilo, že entita je po vytvoření platná.

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a>Použití atributů ověřování v modelu na základě datových poznámek

Datové poznámky, jako jsou povinné nebo MaxLength atributy, lze použít ke konfiguraci EF Core vlastností pole databáze, jak je vysvětleno podrobněji v sekci [mapování tabulky](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) , ale [již nefungují pro ověřování entit v EF Core](https://github.com/aspnet/EntityFrameworkCore/issues/3680) (ani to nedělá). <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> metoda), protože to udělalo od EF 4. x v .NET Framework.

Datové poznámky a <xref:System.ComponentModel.DataAnnotations.IValidatableObject> rozhraní lze i nadále použít k ověřování modelu při vytváření vazby modelu, před vyvoláním akcí kontroleru jako obvykle, ale tento model má být ViewModel nebo DTO, což je MVC nebo rozhraní API, které není doménovým modelem. týkat.

V případě, že se v koncepčním rozdílu vyjasní, `IValidatableObject` můžete i nadále používat datové poznámky a v třídě entit pro ověřování, pokud vaše akce obdrží parametr objektu třídy entity, což se nedoporučuje. V takovém případě se k ověření dojde při vytváření vazby, těsně před vyvoláním akce a můžete zaškrtnout vlastnost ModelState. IsValid kontroleru a ověřit výsledek, ale pak se znovu stane na řadiči, nikoli před uchováním objektu entity v DbContext, stejně jako od EF 4. x.

Můžete přesto implementovat vlastní ověřování v třídě entity pomocí datových poznámek a `IValidatableObject.Validate` metody přepsáním metody SaveChanges DbContext.

Můžete si prohlédnout ukázkovou implementaci pro ověřování `IValidatableObject` entit v [tomto komentáři na GitHubu](https://github.com/aspnet/EntityFrameworkCore/issues/3680#issuecomment-155502539). Tato ukázka neprovádí ověřování na základě atributů, ale měla by být snadno implementovaná pomocí reflexe ve stejném přepsání.

Z bodu DDD se však model domény nejlépe udržuje s využitím výjimek v metodách chování vaší entity nebo implementací specifikací a vzorců oznámení k vynucujení ověřovacích pravidel.

Může být vhodné použít datové poznámky na vrstvě aplikace v třídách ViewModel (namísto doménových entit), které budou přijímat vstupy, aby bylo možné ověřování modelu v rámci vrstvy uživatelského rozhraní. Nicméně to by nemělo být provedeno na základě vyloučení ověřování v rámci doménového modelu.

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Ověření entit implementací vzoru specifikace a způsobu oznámení

Nakonec složitější přístup k implementaci ověřování v doménovém modelu je implementace vzoru specifikace ve spojení se vzorem oznámení, jak je vysvětleno v některých dalších prostředcích, které jsou uvedeny později.

Je třeba uvést, že můžete také použít pouze jeden z těchto vzorů, například ověření ručně pomocí řídicích příkazů, ale použití vzorce oznámení pro skládání a vrácení seznamu chyb ověřování.

### <a name="use-deferred-validation-in-the-domain"></a>Použít odložené ověřování v doméně

Existují různé přístupy k odložení platných ověření v doméně. V rámci své knihy [Implementace návrhu založeného na doméně](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)Vaughn Vernon tyto informace v části věnované ověřování.

### <a name="two-step-validation"></a>Dvoustupňové ověřování

Zvažte také dvoustupňové ověřování. Použijte ověřování na úrovni polí pro příkazy Přenos dat objekty (DTO) a ověřování na úrovni domény uvnitř svých entit. To lze provést vrácením objektu výsledků namísto výjimek, aby bylo snazší řešit chyby ověřování.

Při ověřování pomocí datových poznámek například neduplikujete definici ověřování. Spuštění, ale může být na straně serveru i na straně klienta v případě DTO (příkazy a ViewModels).

## <a name="additional-resources"></a>Další zdroje

- **Rachel Appel. Seznámení s ověřováním modelu ve ASP.NET Core MVC** \
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- **Rick Anderson. Přidání ověřování** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- **Martin Fowlera. Nahrazení výjimek při vygenerování oznámení v ověřováních** \
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- **Specifikace a vzory oznámení** \
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- **Lev Gorodinski. Ověřování v návrhu založeném na doméně (DDD)**  \
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- **Konektor Colin. Ověřování doménového modelu** \
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- **Jimmy Bogard. Ověření v DDD World** \
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> [Předchozí](enumeration-classes-over-enum-types.md)Další
> [](client-side-validation.md)

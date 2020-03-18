---
title: Návrh ověřování ve vrstvě doménového modelu
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Pochopit klíčové pojmy ověření modelu domény.
ms.date: 10/08/2018
ms.openlocfilehash: 98ccc5df84c9f6f402ecbee83b077c806d6a76fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75899670"
---
# <a name="design-validations-in-the-domain-model-layer"></a>Ověření návrhu ve vrstvě modelu domény

V DDD ověřovací pravidla lze považovat za invariants. Hlavní odpovědnost agregace je vynutit invariants napříč změny stavu pro všechny entity v rámci tohoto agregace.

Entity domény by měly být vždy platnými entitami. Existuje určitý počet invariants pro objekt, který by měl být vždy true. Například objekt položky objednávky musí mít vždy množství, které musí být kladné celé číslo, plus název článku a cenu. Vynucení invariants je proto odpovědností entit domény (zejména agregovaného kořenového adresáře) a objekt entity by neměl být schopen existovat bez platnosti. Invariantní pravidla jsou jednoduše vyjádřena jako smlouvy a výjimky nebo oznámení jsou vyvolány, pokud jsou porušeny.

Důvodem je, že mnoho chyb dochází, protože objekty jsou ve stavu, ve které by nikdy nebyly v. Toto je dobré vysvětlení od Greg Young v [on-line diskusi](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/):

Navrhněme, že nyní máme SendUserCreationEmailService, který má UserProfile ... Jak můžeme racionalizovat v této službě, že název není null? Podíváme se na to znovu? Nebo spíše ... prostě se neobtěžujete zkontrolovat a "doufat v to nejlepší" - doufáte, že se někdo obtěžoval ověřit, než vám to pošle. Samozřejmě, pomocí TDD jeden z prvních testů bychom měli psát, je, že když pošlu zákazníka s nulovým názvem, že by měla vyvolat chybu. Ale jakmile začneme psát tyto druhy testů znovu a znovu si uvědomíme ... "Počkejte, jestli jsme nikdy nedovolili, aby se jméno stalo nulovým, neměli bychom všechny tyto testy"

## <a name="implement-validations-in-the-domain-model-layer"></a>Implementace ověření ve vrstvě modelu domény

Ověření jsou obvykle implementována v konstruktorech entit domény nebo v metodách, které mohou entitu aktualizovat. Existuje několik způsobů, jak implementovat ověření, jako je například ověření dat a vyvolání výjimek, pokud se ověření nezdaří. Existují také pokročilejší vzory, jako je například použití specifikace vzor pro ověření a vzor oznámení vrátit kolekci chyb namísto vrácení výjimky pro každé ověření, jak k němu dojde.

### <a name="validate-conditions-and-throw-exceptions"></a>Ověřit podmínky a vyvolat výjimky

Následující příklad kódu ukazuje nejjednodušší přístup k ověření v entitě domény vyvoláním výjimky. V tabulce odkazů na konci této části můžete zobrazit odkazy na pokročilejší implementace na základě vzorů, které jsme diskutovali dříve.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Lepší příklad by demonstroval potřebu zajistit, aby se vnitřní stav nezměnil nebo že došlo ke všem mutacím pro metodu. Například následující implementace by ponechat objekt v neplatném stavu:

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

Pokud je hodnota státu neplatná, první řádek adresy a město již byly změněny. To by mohlo způsobit neplatnost adresy.

Podobný přístup lze použít v konstruktoru entity, vyvolání výjimku a ujistěte se, že entita je platná, jakmile je vytvořena.

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a>Použití ověřovacích atributů v modelu na základě datových poznámk

Datové poznámky, jako jsou atributy Povinné nebo MaxLength, lze použít ke konfiguraci vlastností pole EF Core databáze, jak je podrobně vysvětleno v části [Mapování tabulky,](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) ale [již nefungují pro ověření entity v EF Core](https://github.com/dotnet/efcore/issues/3680) (ani <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> metoda), jak tomu bylo od EF 4.x v rozhraní .NET Framework.

Data anotace <xref:System.ComponentModel.DataAnnotations.IValidatableObject> a rozhraní lze stále použít pro ověření modelu během vazby modelu, před vyvolání akce řadiče jako obvykle, ale tento model má být ViewModel nebo DTO a to je MVC nebo ROZHRANÍ rozhraní se týká není problém modelu domény.

Po odstranění koncepčního rozdílu můžete stále používat datové `IValidatableObject` poznámky a ve třídě entity pro ověření, pokud vaše akce obdrží parametr objektu třídy entity, což se nedoporučuje. V takovém případě dojde k ověření při vazbě modelu, těsně před vyvoláním akce a můžete zkontrolovat vlastnost ModelState.IsValid řadiče, chcete-li zkontrolovat výsledek, ale pak znovu dojde k řadiči, nikoli před uchováním objektu entity v DbContext, stejně jako tomu bylo od EF 4.x.

Stále můžete implementovat vlastní ověření ve třídě entity pomocí `IValidatableObject.Validate` datových anotací a metody přepsáním metody SaveChanges společnosti DbContext.

Ukázkovou implementaci pro ověřování `IValidatableObject` entit můžete zobrazit v tomto [komentáři na GitHubu](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539). Tento vzorek neprovádí ověřování na základě atributů, ale měly by být snadno implementovat pomocí reflexe ve stejném přepsání.

Z hlediska DDD je však model domény nejlépe udržován štíhlý s použitím výjimek v metodách chování entity nebo implementací vzorů specifikace a oznámení k vynucení ověřovacích pravidel.

Může mít smysl používat datové poznámky na aplikační vrstvě ve třídách ViewModel (namísto entit domény), které budou přijímat vstup, aby bylo možné ověřit ověření modelu v rámci vrstvy ui. To by však nemělo být provedeno při vyloučení ověření v rámci modelu domény.

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Ověření entit implementací vzoru specifikace a vzoru oznámení

Nakonec propracovanější přístup k implementaci ověření v modelu domény je implementací specifikace vzor ve spojení se vzorem oznámení, jak je vysvětleno v některých dalších prostředků uvedených později.

Stojí za zmínku, že můžete také použít pouze jeden z těchto vzorů – například ověření ručně s příkazy ovládacího prvku, ale pomocí vzoru oznámení zásobníku a vrátit seznam chyb ověření.

### <a name="use-deferred-validation-in-the-domain"></a>Použít odložené ověření v doméně

Existují různé přístupy k řešení odložené ověření v doméně. Ve své [knize Implementace Domény-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon diskutuje tyto v sekci o validaci.

### <a name="two-step-validation"></a>Dvoustupňové ověření

Zvažte také dvoustupňové ověření. Použijte ověření na úrovni pole u příkazů Objekty přenosu dat (DTO) a ověření na úrovni domény uvnitř entit. Můžete to provést vrácením objektu result namísto výjimek, aby bylo snazší řešit chyby ověření.

Pomocí ověření pole s anotacemi dat například neduplikujete definici ověření. Spuštění však může být na straně serveru i na straně klienta v případě DTO (příkazy a ViewModels, například).

## <a name="additional-resources"></a>Další zdroje

- **Rachel Anetelová. Úvod do validace modelu v ASP.NET Core MVC** \
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- **Rick Anderson. Přidání ověření** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- **Martin Fowler. Nahrazení výtečů výjimky oznámení v ověření** \
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- **Specifikace a vzory oznámení** \
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- **Lev Gorodinski. Ověření v návrhu řízeném doménou (DDD)** \
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- **Colin jack, to je ono. Ověření modelu domény** \
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- **Jimmyho Bogarda. Validace ve světě DDD** \
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> [Předchozí](enumeration-classes-over-enum-types.md)
> [další](client-side-validation.md)

---
title: Návrh vrstvy trvalosti infrastruktury
description: Zjistěte, jak navrhnout vrstvy trvalosti infrastruktury.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/28/2017
ms.openlocfilehash: a0fcaead363e41f0dd02ed1e2ddfc90afb8d0c57
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404470"
---
# <a name="designing-the-infrastructure-persistence-layer"></a>Návrh vrstvy trvalosti infrastruktury

Komponenty trvalosti dat poskytují přístup k datům hostovaným v rámci hranic mikroslužby (to znamená mikroslužeb databáze). Obsahují aktuální implementaci komponent, jako jsou úložiště a [pracovní jednotky](https://martinfowler.com/eaaCatalog/unitOfWork.html) třídy, jako jsou vlastní Entity Framework (EF) <xref:Microsoft.EntityFrameworkCore.DbContext> objekty.

## <a name="the-repository-pattern"></a>Model úložiště

Úložiště jsou třídy nebo komponenty, které provádí zapouzdření logiku potřebnou pro přístup ke zdrojům dat. Centralizujte jsou běžné funkce přístupu k datům, poskytuje lepší udržovatelnost a oddělení infrastruktury nebo technologie používané pro přístup k databázím z vrstvě doménového modelu. Pokud používáte objektově relační mapování (ORM určené) jako Entity Framework, je zjednodušená kód, který musí implementovat, díky LINQ a silných typů. To umožňuje zaměřit se na logiku trvalosti dat, nikoli na datový přístup k vložení.

Model úložiště je dobře zdokumentovaná způsob práce se zdroji dat. V knize [vzory Enterprise Application Architecture](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martina Fowlera popisuje úložiště následujícím způsobem:

> Úložiště provádí úkoly prostředník mezi vrstvami modelu domény a mapování dat v podobným způsobem jako sada domény objektů v paměti. Klientské objekty deklarativně vytvářet dotazy a odeslat je do úložiště pro odpovědi. Entity úložiště zapouzdřuje sadu objektů uložených v databázi a operace, které lze provést s nimi, poskytuje způsob, který je blíž ke vrstvy trvalosti. Úložiště, navíc podporují účel oddělení jasně a v jednom směru závislosti mezi doménou práce a přidělený objem dat nebo mapování.

### <a name="define-one-repository-per-aggregate"></a>Definovat jedno úložiště za agregace

Pro každé agregace nebo agregační kořenový adresář měli byste vytvořit jednu třídu úložiště. V mikroslužbě závislosti na vzorech návrhu řízeného doménou (DDD) by měl být jediným kanál, který použijete k aktualizaci databáze úložiště. Je to proto, že mají vztah 1: 1 s agregační kořenový adresář, který řídí agregaci výstupních podmínek a transakční konzistence. Je možné k dotazování databáze prostřednictvím dalších kanálů (jak vám pomůžou následující přístup modelu CQRS), protože dotazy neměnit stav databáze. Transakční oblasti (to znamená, aktualizace) však musí být vždy kontrolován úložiště a agregační kořenové adresáře.

V podstatě úložiště vám umožní naplnit data v paměti, která pochází z databáze ve formuláři entity domény. Po entity, které jsou v paměti, může se změnit a pak trvalé zpět do databáze do transakce.

Jak je uvedeno dříve, pokud používáte model architektury CQS/CQRS, počáteční dotazy provádějí dotazy na straně mimo doménový model, provádí jednoduché příkazy SQL s použitím Dapperem. Tento přístup je toho mnohem víc, potřebujete flexibilní než úložiště, protože se můžete dotazovat a připojte se k žádné tabulky a tyto dotazy nejsou omezená pravidly agregací. Tato data přejde do prezentační vrstvy nebo klientské aplikace.

Pokud uživatel provede změny, data, která mají být aktualizovány pochází z klienta aplikace nebo prezentační vrstvy do vrstvy aplikace (jako je například služba webového rozhraní API). Přijmout příkaz s daty v obslužná rutina příkazu, použijete k získání dat, které chcete aktualizovat z databáze úložiště. Aktualizujete v paměti s informacemi o byla dokončena s příkazy, a pak přidat nebo aktualizovat data (domény entity) v databázi pomocí transakce.

Mějte na paměti, že tento pouze jedno úložiště by měl definovat pro kořenovém adresáři každého agregace, jak je znázorněno v obrázek 9-17. K dosažení cíle agregační kořenových zachovat transakční konzistenci mezi všechny objekty v rámci agregace, měli byste nikdy vytvořit úložiště pro každou tabulku v databázi.

![](./media/image18.png)

**Obrázek 9-17**. Vztah mezi úložišť, agregace a databázových tabulek

### <a name="enforcing-one-aggregate-root-per-repository"></a>Vynucování jeden kořenový agregační na úložiště

Může být užitečné k implementaci návrhu úložiště tak, že vynutí toto pravidlo, že by měl mít jenom agregační kořeny úložišť. Můžete vytvořit typ obecného nebo základního úložiště, který omezí typ entity funguje s zajistit, že mají `IAggregateRoot` rozhraní značek.

Každá třída úložiště implementované ve vrstvě infrastruktury implementuje proto svůj vlastní kontrakt nebo rozhraní, jak je znázorněno v následujícím kódu:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

Každé rozhraní konkrétního úložiště implementuje obecné rozhraní IRepository:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Ale lepší způsob, jak kód vynutit konvenci, že každé úložiště se vztahuje k jedné agregace je implementace typu obecného úložiště. Tímto způsobem je explicitní, že používáte úložiště cílit na konkrétní agregace. To jde snadno udělat pomocí implementace obecný `IRepository` základní rozhraní, jako v následujícím kódu:

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Vzor úložiště usnadňuje testování vaší aplikace logiky

Vzor úložiště umožňuje snadno testujte aplikace s testy jednotek. Mějte na paměti, že testy jednotek pouze test kód, ne na infrastrukturu, tak úložiště abstrakce zjednodušují dosažení tohoto cíle.

Jak je uvedeno v předchozí části, se doporučuje definovat a umístěte rozhraní úložiště ve vrstvě doménového modelu, aplikační vrstvy, jako je například vaše webové rozhraní API mikroslužby nezávisí přímo na vrstvě infrastruktury kde jsme implementovali třídy skutečné úložiště. To a využitím vkládání závislostí do kontrolerů webového rozhraní API, můžete implementovat mock úložišť, které vracejí falešné data namísto dat z databáze. Tento přístup oddělení umožňuje vytvořit a spustit testy jednotky, které můžete testovat logiku aplikace bez nutnosti připojení k databázi.

Připojení k databázím může selhat a důležitější je, provozování testů pro databázi je chybný pro dva důvody. Nejdřív může trvat dlouhou dobu z důvodu velkého počtu testů. Za druhé může být záznamů databáze změnit a ovlivnit výsledky testů, takže se nemusí být konzistentní vzhledem k aplikacím. Testování proti databázi není testování částí, ale o test integrace. Měli byste mít mnoho testů jednotek rychlé spuštění, ale méně integrace testy proti databáze.

Z hlediska oddělení oblastí zájmu pro testování částí pracuje svoji logiku domény entity v paměti. Předpokládá se, že ty dodal třídu úložiště. Jakmile svoji logiku upraví domény entity, předpokládá se, že třídu úložiště bude správně uložit. Důležitý bod je vytvoření testů jednotek pro doménový model a jeho logiku domény. Agregační kořeny jsou hranice hlavní konzistence v DDD.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Rozdíl mezi použitému vzoru a starší verze třídy (třídy DAL) vzor přístupu k datům

Datový objekt přímo provádí operace přístupu a trvalost dat využívající službu storage. Úložiště označí data s operacemi, které chcete provést v paměti objektu pracovní jednotka (stejně jako v EF při použití <xref:Microsoft.EntityFrameworkCore.DbContext> třídy), ale tyto aktualizace se neprovádí hned.

Určitou jednotku práce se označuje jako jedna transakce, která zahrnuje více vložení, aktualizace nebo odstranění operace. Jednoduše řečeno znamená to, že pro konkrétního uživatele akce, jako je registrace na webu, insert, update a delete transakce jsou zpracovány v rámci jedné transakce. To je mnohem efektivnější než zpracování více transakcí databáze chattier způsobem.

Tyto trvalost provádí více operací se později v rámci jedné akce při příkazy kódu z aplikační vrstvy. Rozhodnutí o aplikování změn v paměti úložiště skutečné databáze je obvykle na základě [pracovní jednotky vzor](https://martinfowler.com/eaaCatalog/unitOfWork.html). V EF, vzor pracovní jednotky je implementovaný jako <xref:Microsoft.EntityFrameworkCore.DbContext>.

V mnoha případech se může tento vzor nebo způsob použití operací s úložištěm zvýšit výkon aplikace a snížení rizika vzniku nekonzistence. Také snižuje transakcí, zablokování v tabulkách databáze, protože všechny odpovídající operace usilujeme o to jako součást jedné transakce. To je mnohem efektivnější porovnání provádí mnoho operací izolované databázi. Vybrané ORM proto můžete optimalizovat spuštění proti databázi seskupením několika akcí aktualizace v rámci jedné transakce, na rozdíl od mnoha malých a samostatné transakce spuštění.

### <a name="repositories-shouldnt-be-mandatory"></a>Úložiště by neměly být povinné

Vlastní úložiště jsou užitečné z důvodů uvedených výše, tedy přístup pro objednávání mikroslužeb v aplikaci eShopOnContainers. Však není základní vzor, který se má implementovat v návrhu DDD nebo dokonce obecně vývoj na platformě .NET.

Například Jimmy Bogard, při poskytnutí zpětné vazby s přímým přístupem k této příručce se říká, že následující:

> To bude pravděpodobně Moje největší zpětnou vazbu. Nejsem skutečně ventilátor úložišť, zejména proto, že skrývají důležité podrobnosti základní mechanismus trvalosti. Jeho proč můžu získat MediatR příkazy příliš. Můžu plně využijte potenciál vrstvy trvalosti a nasdílení změn do mé agregační kořeny toto chování domény. Nechci obvykle napodobení Moje úložiště – stále je potřeba tuto integraci test s Opravdová věc. Přechod CQRS určená, že nebyly k dispozici skutečně potřeba pro úložiště víc.

Úložiště jsou užitečné, ale nejsou důležité pro váš DDD ve způsobu, jakým agregační vzor a bohaté doménový model se. Proto se ale nemusíte používat úložiště vzor, podle svých potřeb.

## <a name="the-specification-pattern"></a>Vzor specifikace

Vzor specifikace (úplného názvu bude vzor dotazu specification) je vzor DDD navržený místem, kde můžete ukládat definice dotazu s volitelné, řazení a stránkování logiku.

Vzor specifikace definuje dotaz v objektu. Například k zapouzdření stránkovaného dotaz, který vyhledá některé produkty, můžete vytvořit `PagedProduct` specifikace, která přebírá nezbytné vstupní parametry, jako například `pageNumber`, `pageSize`, `filter`atd. Poté, v rámci metody jakékoli úložiště (obvykle List() přetížení) se bude přijímat `ISpecification` a spusťte dotaz očekávané založené na specifikaci.

Existuje více výhod tohoto přístupu:

- Specifikace má název (na rozdíl od jen hromada LINQ – výrazy), které můžete diskutovat o.

- Specifikace může být jednotka testovány v izolaci Ujistěte se, že je správný. Můžete použít také snadno opakovaně, pokud potřebujete podobné chování. Například na akci zobrazení MVC a webového rozhraní API akce i v různých služeb.

- Specifikace je také možné popisující tvar dat, který se má vrátit, tak, aby dotazy mohou vracet pouze data jsou povinné. Tím se eliminuje potřebu opožděné načtení webové aplikace, což obvykle nedoporučujeme, a pomáhá udržovat implementace úložiště z stávají nepotřebná data o tyto podrobnosti.

Příklad obecného specifikace rozhraní je následující kód z [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).

```csharp
// https://github.com/dotnet-architecture/eShopOnWeb
public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

V nadcházejících částech popisují, jak implementovat vzor specifikace s EF Core 2.x a jak ji používat z jiné třídy úložiště.

> [!IMPORTANT]
> Specifikace vzor je starý vzor, který je možné implementovat mnoha různými způsoby, stejně jako v následujících zdrojích. Jako vzor/nápad je vhodné vědět, ale mějte na paměti, starší implementace, které nejsou využít moderní jazyk funkce, jako je Linq a výrazy starší přístupy.

## <a name="additional-resources"></a>Další zdroje

### <a name="the-repository-pattern"></a>Model úložiště

- **Model úložiště**
  [https://deviq.com/repository-pattern/](https://deviq.com/repository-pattern/)

- **EDWARD Hieatt a Rob mi. Model úložiště.**
  [_https://martinfowler.com/eaaCatalog/repository.html_](https://martinfowler.com/eaaCatalog/repository.html)

- **Model úložiště**
  [_https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)_](https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10))

- **Eric Evans. Návrhy řízené doménou: Použití složitosti srdce softwaru.** (Kniha; obsahuje diskusi o vzor úložiště) [_https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/_](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="unit-of-work-pattern"></a>Jednotka pracovní postup

- **Martina Fowlera. Jednotka pracovní postup.**
  [_https://martinfowler.com/eaaCatalog/unitOfWork.html_](https://martinfowler.com/eaaCatalog/unitOfWork.html)

- **Implementace úložiště a jednotky pracovních vzorů v aplikaci ASP.NET MVC**
  [_https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application_](https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

### <a name="the-specification-pattern"></a>Vzor specifikace

- **Specifikace vzor.**
  [_https://deviq.com/specification-pattern/_](https://deviq.com/specification-pattern/)

- **Evans, Eric (2004). Návrhu na základě domény. Addison Wesley. p. 224.**

- **Specifikace. Martina Fowlera**
  [_https://www.martinfowler.com/apsupp/spec.pdf/_](https://www.martinfowler.com/apsupp/spec.pdf)

>[!div class="step-by-step"]
[Předchozí](domain-events-design-implementation.md)
[další](infrastructure-persistence-layer-implemenation-entity-framework-core.md)

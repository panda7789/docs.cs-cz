---
title: Navrhování vrstvu trvalosti infrastruktury
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Navrhování vrstvu trvalosti infrastruktury
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/08/2017
ms.openlocfilehash: 9da1020ac5b43971a8f976c518f4537bec866c26
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105843"
---
# <a name="designing-the-infrastructure-persistence-layer"></a>Navrhování vrstvu trvalosti infrastruktury

Součásti trvalosti dat poskytnout přístup k datům hostovaným v rámci hranice mikroslužbu (to znamená, databáze mikroslužbu). Obsahují skutečné implementace komponenty, například úložiště a [jednotky práce](https://martinfowler.com/eaaCatalog/unitOfWork.html) třídy, jako jsou vlastní EF DBContexts.

## <a name="the-repository-pattern"></a>Vzor úložiště

Úložiště jsou třídy nebo součásti, které zapouzdřují logiku potřebnou k přistupovat ke zdrojům dat. Jejich centralizovat běžné funkce přístupu dat, poskytuje lepší udržovatelnosti a oddělení infrastrukturu nebo technologie používané pro přístup k databázím z vrstvy modelu domény. Pokud používáte ORM jako Entity Framework, je zjednodušená kód, který musí být implementována, díky LINQ a silného typování. Tento přístup umožňuje zaměřit se na logice trvalosti dat, ne na data k vložení.

Vzor úložiště je dobře zdokumentovaných způsob práce se zdrojem dat. V seznamu [vzory Architektura aplikace Enterprise](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martin Fowler popisuje úložiště následujícím způsobem:

Úložiště provádí úlohy zprostředkovatele mezi domény modelu vrstev a mapování dat, který funguje podobným způsobem sadu objektů domény v paměti. Objekty klienta deklarativně vytvořit dotazy a odeslat je do úložiště pro odpovědi. Úložiště koncepčně, zapouzdří sadu objektů, které jsou uloženy v databázi a operací, které lze provést na, poskytuje tak, že bude co nejblíže ke vrstvu trvalosti. Úložiště, navíc podporují účel jasně a v jednom směru oddělení závislost mezi pracovní domény a požadavky na data nebo mapování.

### <a name="define-one-repository-per-aggregate"></a>Definovat jeden úložiště pro agregace

Pro každý kořenový agregační nebo agregační byste měli vytvořit jednu třídu úložiště. Mikroslužbu, na základě způsobů funguje na základě domény musí být pouze kanál, který byste měli použít k aktualizaci databáze úložiště. Je to proto, že jsou v relaci s agregační kořenový adresář, který řídí výstupních podmínek na agregaci a transakční konzistence. Je to v pořádku pro dotazování databáze prostřednictvím jiné kanály (jako je tomu následující CQRS přístup), protože dotazy neměňte stav databáze. Ale oblasti transakcí – aktualizace – musí být vždy kontrolován úložiště a agregační kořenové adresáře.

V podstatě úložiště vám umožní naplnit data v paměti, který přichází z databáze ve formě entity domény. Jakmile entity, které jsou v paměti, může být změnit a pak trvalé zpět do databáze pomocí transakce.

Jak jsme uvedli dříve, pokud používáte CQS/CQRS architekturní vzor, provede počáteční dotazy straně dotazy z modelu domény, provádí pomocí Dapper jednoduché příkazů SQL. Tento přístup je mnohem víc, stačí flexibilní než úložiště, protože můžete vyhledat a připojit k žádné tabulky, a tyto dotazy nejsou omezeny pravidla z agregace. Tato data budou moct prezentační vrstvy nebo klientské aplikace.

Pokud uživatel provede změny, aktualizace dat bude pocházet z klienta aplikace nebo prezentační vrstvy do vrstvy aplikace (například webového rozhraní API služby). Jakmile se zobrazí příkaz (s daty) v obslužná rutina příkazu, použijete úložiště získat data, která chcete aktualizovat z databáze. Aktualizujete v paměti s informacemi o byla dokončena s příkazy, a pak přidáte nebo aktualizujete data (domény entity) v databázi pomocí transakce.

Pamatovat na to, že pouze jeden úložiště by měl být definován pro každý agregační kořenový adresář, jak je znázorněno v obrázek 9-17. K dosažení cíle agregační kořenové zachování transakční konzistence mezi všechny objekty v rámci agregace, měli byste nikdy vytvořit úložiště pro každou tabulku v databázi.

![](./media/image18.png)

**Obrázek 9-17**. Vztah mezi úložiště, agregace a tabulek databáze

### <a name="enforcing-one-aggregate-root-per-repository"></a>Vynucování jeden kořenový agregační na úložiště

Může být užitečné k implementaci návrhu úložiště tak, že vynucuje pravidlo, že pouze agregační kořenových certifikačních autorit by měl mít úložiště. Můžete vytvořit úložiště obecné nebo základní typ, který omezí typ entity, které funguje s zajistit, že mají rozhraní IAggregateRoot značky.

Každá třída úložiště implementována ve vrstvě infrastruktury implementuje proto vlastní kontrakt nebo rozhraní, jak je znázorněno v následujícím kódu:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
```

Každé rozhraní konkrétní úložiště implementuje obecné rozhraní IRepository:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Však lepší způsob, jak mají kód vynutit konvence, každý úložiště by měl mít relace k jedné agregaci by implementovat typu Obecné úložiště tak, aby byl explicitní, že používáte úložiště pro konkrétní agregace. Můžete snadno provést implementací této obecné v IRepository základní rozhraní, jako v následujícím kódu:

```csharp
  public interface IRepository<T> where T : IAggregateRoot
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Vzor úložiště usnadňuje testování vaší aplikace logiky

Vzor úložiště umožňuje snadno testování vaší aplikace pomocí jednotkových testů. Mějte na paměti, že testy jednotek pouze zkušební kód, není infrastrukturu, tak abstrakce úložiště usnadňují dosažení tohoto cíle.

Jak je uvedeno v předchozí části, se doporučuje definovat a umístit rozhraní úložiště vrstva modelu domény, aplikační vrstvu (například vaše mikroslužbu webového rozhraní API) nezávisí přímo na vrstvě infrastruktury kde máte implementované tříd skutečné úložiště. Díky tomuto a využitím vkládání závislostí v řadiče webové rozhraní API, můžete implementovat imitované úložiště, které vracejí místo data falešných dat z databáze. Že odpojeného přístup umožňuje vytvořit a spuštění jednotky testy, které můžete testovat logiku aplikace bez nutnosti připojení k databázi.

Připojení k databázím může selhat a důležitější, spuštěn stovky testy s databází je chybný. dvou důvodů. První může trvat mnoho času z důvodu velkého počtu testy. Druhý záznamů databáze může změnit a ovlivnit výsledky testů, takže se nemusí být v souladu. Testování v databázi není jednotka testy ale integrační testování. Měli byste mít mnoho testy jednotek rychlé spuštění, ale méně integrace testy s databází.

Z hlediska oddělené oblasti zájmu pro testy logika funguje na domény entity v paměti. Předpokládá se, že se že má doručit třídu úložiště, ty. Jakmile logika upraví entity domény, předpokládá se, že třídu úložiště bude správně uložit. Zde důležité je, chcete-li vytvářet testy částí proti modelu domény a jeho logiku domény. Agregační kořeny jsou hlavní konzistence hranice v DDD.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Rozdíl mezi použitému vzoru a starší verze třídy (třídy DAL) vzor přístupu k datům

Datový objekt přístup přímo provádí operace přístupu a trvalosti dat pro úložiště. Úložiště značky, které dat pomocí operace, které chcete provést v paměti jednotky práce objektu (jako EF při použití DbContext), ale tyto aktualizace se neprovádí okamžitě.

Jednotka práce, se označuje jako jediná transakce, který zahrnuje několik vložení, aktualizaci nebo odstranění operace. Jednoduše řečeno znamená to, že pro akci konkrétního uživatele (například registrace na webu), insert, update a delete transakce jsou zpracovávány v rámci jedné transakce. Toto je efektivnější než zpracování více transakcí databáze chattier způsobem.

Tyto více trvalost operací později v rámci jedné akce při kódu z aplikační vrstvu příkazů ho. Rozhodnutí o provádění změn v paměti pro úložiště skutečná databáze obvykle závisí na [jednotky práce vzor](https://martinfowler.com/eaaCatalog/unitOfWork.html). V EF vzoru pracovní jednotky je implementovaný jako DBContext.

V řadě případů můžete tento vzor nebo způsob použití operace u úložiště zvýšit výkon aplikace a omezit možnost nekonzistence. Také zmenšuje transakce blokování v tabulkách databáze, protože všechny zamýšlené operace potvrzeny jako součást jedné transakce. Toto je efektivnější oproti provádění mnoho izolované operací v databázi. Vybrané ORM tedy moci optimalizovat provádění proti dané databázi seskupením několik akcí aktualizace v rámci stejné transakci oproti spuštěních mnoho malých a samostatné transakce.

### <a name="repositories-should-not-be-mandatory"></a>Úložiště by neměl být povinné

Vlastní úložiště jsou užitečné z důvodů citovalo dříve a který je přístup pro řazení mikroslužbu v eShopOnContainers. Je však není základní vzor implementovat v návrhu DDD nebo dokonce obecně vývoj v rozhraní .NET.

Například uvedená Jimmy Bogard, při poskytování zpětné vazby přímé Tato příručka následující:

Toto budete pravděpodobně Moje největších zpětnou vazbu. Nejsem skutečně ventilátor úložišť, především, protože se skrýt důležité podrobnosti o základní mechanismus trvalosti. Jeho proč vrátit pro MediatR pro příkazy, příliš. I použít potenciál vrstvu trvalosti a vkládání daná chování domény do mé agregační kořenových certifikačních autorit. Model Moje úložiště nechci obvykle – je třeba mít této integrace testu s Opravdová věc. Budete CQRS určená, že nebyly k dispozici skutečně potřeba úložiště víc.

Jsme užitečné úložiště, ale nemůžeme na vědomí, že nejsou důležité pro vaši DDD, způsobem, jakým jsou agregační vzor a modelu bohaté domény. Proto použití vzoru úložiště, nebo Ne, jak můžete vidět odpovídat.

## <a name="the-specification-pattern"></a>Specifikace vzor

Vzor specifikace (plným názvem být specifikaci dotazu vzor) je vzor návrhu Domain-Driven určená jako místo, kde můžete ukládat definici dotazu s volitelné, řazení a stránkování logiku.

Vzor specifikace definuje dotazu v objektu. Chcete-li zapouzdření stránkové dotaz, který hledá některé produkty, například můžete vytvořit specifikaci PagedProduct, která se mají potřebné vstupní parametry (pageNumber pageSize, filtr, atd.). Poté v libovolné metody úložiště (obvykle přetížení List()) by přijmout ISpecification a spusťte očekávané dotaz založený na této specifikaci.

Existuje několik výhod tohoto přístupu:

* Specifikace má název (na rozdíl od právě bunch LINQ – výrazy), který lze diskutovat o o.

* Specifikace může být jednotka otestována izolace Ujistěte se, že je správný. Můžete se také snadno znovu, pokud potřebujete podobné chování. Například na akci zobrazení MVC a akce webového rozhraní API a také různé služby.

* Specifikaci lze také použít k popisu tvaru data, která mají být vráceny, tak, aby dotazy mohou vracet pouze data, se vyžaduje. Tím se eliminuje potřeba opožděného načítání webových aplikací, (což je obvykle není vhodné) a pomáhá udržovat implementace úložiště z stal zaplněny, tyto podrobnosti.

Následující kód je například obecné specifikace rozhraní [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb ).

```csharp
// https://github.com/dotnet-architecture/eShopOnWeb 
public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

V nadcházejících částech se vysvětluje, jak implementovat vzor specifikace s Entity Framework Core 2.0 a způsobu jeho použití z libovolné třídy úložiště.

**Důležité upozornění:** specifikace vzor je starý vzor, který můžou se implementovat v mnoha různými způsoby, stejně jako v následujících zdrojích. Jako vzor nebo nápad jsou dobré vědět, ale pozor starší implementací, které nejsou využívat výhod moderní jazyk funkcí, jako Linq a výrazy starší přístupy.

## <a name="additional-resources"></a>Další zdroje

### <a name="the-repository-pattern"></a>Vzor úložiště

-   **EDWARD Hieatt a Rob mi. Vzor úložiště.**
    [*https://martinfowler.com/eaaCatalog/repository.html*](https://martinfowler.com/eaaCatalog/repository.html)

-   **Vzor úložiště**
    [*https://msdn.microsoft.com/library/ff649690.aspx*](https://msdn.microsoft.com/library/ff649690.aspx)

-   **Použitému vzoru: Data abstrakce**
    [*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)

-   **Zařízení Evans Erica. Řízené domény návrhu: Boji se složitostí při vysílat softwaru.** (Sešit; zahrnuje diskuzi o vzoru úložiště) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="unit-of-work-pattern"></a>Jednotka práce vzor

-   **Martin Fowler. Jednotka práce vzor.**
    [*https://martinfowler.com/eaaCatalog/unitOfWork.html*](https://martinfowler.com/eaaCatalog/unitOfWork.html)

<!-- -->

-   **Implementace úložiště a jednotky pracovních vzorů v aplikaci ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

### <a name="the-specification-pattern"></a>Specifikace vzor

-   **Specifikace vzor.**
    [*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)

-   **Zařízení Evans Erica (2004). Doména řízené návrhu. Addison-Wesley. p. 224.**

-   **Specifikace. Martin Fowler**
    [*https://www.martinfowler.com/apsupp/spec.pdf/*](https://www.martinfowler.com/apsupp/spec.pdf)

>[!div class="step-by-step"]
[Předchozí](domain-events-design-implementation.md)
[další](infrastructure-persistence-layer-implemenation-entity-framework-core.md)

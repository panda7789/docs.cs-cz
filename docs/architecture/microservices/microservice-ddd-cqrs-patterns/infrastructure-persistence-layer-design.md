---
title: Návrh vrstvy trvalosti infrastruktury
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Prozkoumejte vzor úložiště v návrhu vrstvy trvalosti infrastruktury.
ms.date: 10/08/2018
ms.openlocfilehash: f1c5df1cc5672760374610a416ae22b45cd76c25
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737940"
---
# <a name="design-the-infrastructure-persistence-layer"></a>Návrh vrstvy trvalosti infrastruktury

Komponenty Trvalost dat poskytují přístup k datům hostovaným v rámci hranic mikroslužby (tj. databáze mikroslužeb). Obsahují skutečnou implementaci komponent, jako jsou úložiště a [jednotky pracovních](https://martinfowler.com/eaaCatalog/unitOfWork.html) tříd, jako jsou například vlastní Entity Framework (EF) <xref:Microsoft.EntityFrameworkCore.DbContext> objekty. EF DbContext implementuje jak úložiště, tak i pracovní jednotky.

## <a name="the-repository-pattern"></a>Vzor úložiště

Úložiště jsou třídy nebo komponenty, které zapouzdřují logiku potřebnou k přístupu ke zdrojům dat. Slouží k centralizaci běžných funkcí přístupu k datům, což zajišťuje lepší udržovatelnost a odpojuje infrastrukturu nebo technologii používanou pro přístup k databázím z vrstvy doménového modelu. Použijete-li objektově-relační mapovači (ORM), jako je Entity Framework, kód, který musí být implementován, je zjednodušený, díky LINQ a silnému psaní. To vám umožní soustředit se na logiku trvalosti dat, a ne na domovníing pro přístup k datům.

Vzor úložiště je dobře dokumentovaný způsob práce se zdrojem dat. V rámci příručky k [architektuře podnikových aplikací](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/)Fowlera Martin popisuje úložiště následujícím způsobem:

> Úložiště provádí úlohy zprostředkovatele mezi vrstvami doménového modelu a mapováním dat a funguje podobným způsobem jako sada doménových objektů v paměti. Klientské objekty deklarativně sestavují dotazy a odesílají je do úložišť pro odpovědi. V koncepčním případě úložiště zapouzdřuje sadu objektů uložených v databázi a operace, které lze v nich provést, a poskytuje tak způsob, který je blíže vrstvě trvalosti. Úložiště také podporují účely oddělení, jasně i v jednom směru závislost mezi pracovní doménou a přidělením nebo mapováním dat.

### <a name="define-one-repository-per-aggregate"></a>Definování jednoho úložiště na agregaci

Pro každý agregovaný nebo agregovaný kořenový adresář byste měli vytvořit jednu třídu úložiště. V mikroslužbě založené na vzorcích pro návrh na základě domén (DDD) by měl být jediným kanálem, který byste měli použít k aktualizaci databáze, úložiště. Důvodem je, že mají relaci 1:1 s agregovaným kořenovým adresářem, který řídí invariantování agregace a transakční konzistenci. Je možné se dotazovat databáze prostřednictvím jiných kanálů (jak můžete postupovat podle CQRS přístupu), protože dotazy nemění stav databáze. Nicméně transakční oblast (tj. aktualizace) musí být vždy ovládána úložištěm a agregovanými kořeny.

V podstatě umožňuje úložiště naplnit data v paměti, která pocházejí z databáze, ve formě doménových entit. Jakmile jsou entity v paměti, můžou se změnit a pak trvale uložit do databáze prostřednictvím transakcí.

Jak bylo uvedeno dříve, pokud používáte model architektury CQS/CQRS, počáteční dotazy se provádějí pomocí dotazů na straně sebe z doménového modelu, které provádí jednoduché příkazy SQL pomocí Dapperem. Tento přístup je mnohem flexibilnější než u úložišť, protože můžete zadávat dotazy a spojit se s libovolnými tabulkami, které potřebujete, a tyto dotazy nejsou omezeny pravidly z agregací. Tato data přecházejí do prezentační vrstvy nebo klientské aplikace.

Pokud uživatel provede změny, data, která mají být aktualizována, pocházejí z klientské aplikace nebo prezentační vrstvy do aplikační vrstvy (například služby webového rozhraní API). Když obdržíte příkaz v obslužné rutině příkazu, použijete úložiště k získání dat, která chcete aktualizovat z databáze. Aktualizujete ho v paměti daty, která byla předána pomocí příkazů, a pak v databázi přidáte nebo aktualizujete data (entity domény) v rámci transakce.

Je důležité se znovu zdůraznit, že byste měli definovat jenom jedno úložiště pro každý agregovaný kořen, jak je znázorněno na obrázku 7-17. Aby bylo možné dosáhnout cíle agregovaného kořene pro zachování transakční konzistence mezi všemi objekty v rámci agregace, neměli byste nikdy vytvořit úložiště pro každou tabulku v databázi.

![Diagram znázorňující vztahy domény a jiné infrastruktury](./media/infrastructure-persistence-layer-design/repository-aggregate-database-table-relationships.png)

**Obrázek 7-17**. Vztah mezi úložišti, agregacemi a databázovými tabulkami

Výše uvedený diagram znázorňuje vztahy mezi doménami a vrstvami infrastruktury: agregace kupující závisí na IBuyerRepository a pořadí agregace závisí na rozhraních IOrderRepository, tato rozhraní se implementují ve vrstvě infrastruktury. v odpovídajících úložištích, které jsou závislé na UnitOfWork, se také implementují, které přistupují k tabulkám v datové vrstvě.

### <a name="enforce-one-aggregate-root-per-repository"></a>Vysazení jednoho agregovaného kořene na úložiště

To může být užitečné pro implementaci návrhu úložiště takovým způsobem, že vynutilo pravidlo, že by měli mít úložiště jenom agregované kořeny. Můžete vytvořit obecný nebo základní typ úložiště, který omezuje typ entit, se kterými pracuje, aby bylo zajištěno, že mají rozhraní `IAggregateRoot` značky.

Proto každá třída úložiště implementovaná na infrastruktuře infrastruktury implementuje svůj vlastní kontrakt nebo rozhraní, jak je znázorněno v následujícím kódu:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

Každé konkrétní rozhraní úložiště implementuje obecné rozhraní IRepository:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Lepší způsob, jak mít kód vyhovět konvenci, že každé úložiště souvisí s jednou agregací, je implementovat obecný typ úložiště. Tímto způsobem je explicitní použít úložiště k zaměření na konkrétní agregaci. To lze snadno provést implementací obecného `IRepository` základního rozhraní, jak je uvedeno v následujícím kódu:

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Vzor úložiště usnadňuje testování logiky aplikace.

Vzor úložiště vám umožňuje snadno testovat aplikace pomocí testů jednotek. Mějte na paměti, že testy jednotek testují pouze kód, nikoli infrastrukturu, takže abstrakce úložiště usnadňují dosažení tohoto cíle.

Jak je uvedeno v předchozí části, doporučuje se definovat a umístit rozhraní úložiště do vrstvy doménového modelu, takže aplikační vrstva, jako je například vaše mikroslužba webového rozhraní API, nezávisí přímo na vrstvě infrastruktury, ve které jste implementovali. skutečné třídy úložiště Tímto způsobem a použitím injektáže závislosti v řadičích webového rozhraní API můžete implementovat napodobná úložiště, která vracejí falešná data namísto dat z databáze. Tento oddělený přístup umožňuje vytvořit a spustit testy jednotek, které se zaměřují na logiku vaší aplikace bez nutnosti připojení k databázi.

Připojení k databázím může selhat a důležitější je, že spouštění stovek testů proti databázi je ze dvou důvodů špatné. Za prvé může trvat dlouhou dobu z důvodu velkého počtu testů. Za druhé se můžou záznamy databáze změnit a ovlivnit výsledky testů, aby mohly být nekonzistentní. Testování proti databázi není jednotkovým testem, ale s testem integrace. Měli byste mít spoustu testů jednotek spuštěných rychleji, ale méně integračních testů pro databáze.

V souvislosti s oddělením potíží s testováním jednotek vaše logika funguje na doménových entitách v paměti. Předpokládá, že třída úložiště je dodala. Jakmile vaše logika upraví entity domény, předpokládá se, že třída úložiště bude ukládat správně. Důležitým bodem je postup, jak vytvořit testování částí pro doménový model a jeho doménovou logiku. Agregované kořeny jsou hlavní hranice konzistence v DDD.

Úložiště implementovaná v eShopOnContainers spoléhají EF Core na DbContext implementaci úložiště a pracovní jednotky pracovních schémat pomocí sledování změn, takže tyto funkce neduplikují.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Rozdíl mezi vzorem úložiště a vzorem třídy pro přístup k datům starší verze (třída DAL)

Objekt pro přístup k datům přímo provádí operace přístupu k datům a trvalých operací proti úložišti. Úložiště označí data operacemi, které chcete provést, v paměti objektu pracovní jednotky (jako v EF při použití třídy <xref:Microsoft.EntityFrameworkCore.DbContext>), ale tyto aktualizace nejsou okamžitě provedeny do databáze.

Pracovní jednotka je označována jako jediná transakce, která zahrnuje několik operací vložení, aktualizace nebo odstranění. V jednoduchých případech to znamená, že pro konkrétní akci uživatele, jako je například registrace na webu, jsou všechny operace vložení, aktualizace a odstranění zpracovávány v rámci jedné transakce. To je efektivnější než zpracování více transakcí databáze chattier způsobem.

Tyto vícenásobné operace trvalosti jsou prováděny později v rámci jedné akce, když kód z aplikační vrstvy je příkaz. Rozhodnutí o použití změn v paměti pro skutečné úložiště databáze je obvykle založené na [modelu pracovní jednotky](https://martinfowler.com/eaaCatalog/unitOfWork.html). V EF je pracovní jednotka modelu implementována jako <xref:Microsoft.EntityFrameworkCore.DbContext>.

V mnoha případech může tento model nebo způsob použití operací s úložištěm zvýšit výkon aplikace a snížit možnost nekonzistencí. Také snižuje blokování transakcí v databázových tabulkách, protože všechny zamýšlené operace jsou potvrzeny jako součást jedné transakce. To je efektivnější pro porovnání se spouštěním velkého množství izolovaných operací s databází. Proto vybraný ORM může optimalizovat spouštění proti databázi seskupením několika akcí aktualizace v rámci stejné transakce, na rozdíl od mnoha malých a oddělených spuštění transakcí.

### <a name="repositories-shouldnt-be-mandatory"></a>Úložiště by neměla být povinná

Vlastní úložiště jsou užitečná z výše uvedených důvodů a to je přístup k řazení mikroslužby v eShopOnContainers. Nejedná se ale o zásadní vzor, který by bylo možné implementovat v rámci návrhu DDD nebo dokonce i při obecném vývoji pro .NET.

Například Jimmy Bogard při poskytování přímé zpětné vazby k této příručce říkáme následující:

> To pravděpodobně bude největší zpětnou vazbu. Nerozumím ventilátoru úložišť, hlavně protože skrývají důležité podrobnosti základního mechanismu trvalosti. Z tohoto důvodu je to pro příkazy MediatR. Můžu použít plný výkon vrstvy trvalosti a všechny tyto vlastnosti domény nahrajte do agregovaných kořenů. Nechci obvykle nastavovat moje úložiště – I přesto je potřeba mít tento test integrace s skutečnou věc. CQRS znamenalo, že ještě nepotřebujeme nějaká úložiště.

Úložiště můžou být užitečná, ale pro návrh DDD nejsou kritická, a to tak, jak jsou agregovaným vzorem a bohatým doménovým modelem. Proto použijte vzor úložiště, a to podle potřeby. V takovém případě budete používat model úložiště vždy, když použijete EF Core i když v tomto případě úložiště pokrývá celý mikroslužbu nebo ohraničený kontext.

## <a name="additional-resources"></a>Další zdroje

### <a name="repository-pattern"></a>Vzor úložiště

-  \ **vzoru úložiště**
  <https://deviq.com/repository-pattern/>

- **Edward Hieatt a Rob mě. Vzor úložiště** \
  <https://martinfowler.com/eaaCatalog/repository.html>

-  \ **vzoru úložiště**
  <https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)>

- **Eric Evans. Návrh založený na doméně: řešení složitosti na srdce softwaru.** (Kniha; zahrnuje diskusi ke vzoru úložiště) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="unit-of-work-pattern"></a>Vzor pracovní jednotky

- **Martin Fowlera. Model pracovní jednotky.** \
  <https://martinfowler.com/eaaCatalog/unitOfWork.html>

- **Implementace vzorového úložiště a pracovní jednotky v aplikaci ASP.NET MVC** \
  <https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

>[!div class="step-by-step"]
>[Předchozí](domain-events-design-implementation.md)
>[Další](infrastructure-persistence-layer-implemenation-entity-framework-core.md)

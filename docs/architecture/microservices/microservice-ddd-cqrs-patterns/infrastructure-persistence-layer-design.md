---
title: Návrh vrstvy trvalosti infrastruktury
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Prozkoumejte vzor úložiště v návrhu vrstvy trvalosti infrastruktury.
ms.date: 10/08/2018
ms.openlocfilehash: e10c8c1569089d5c8274df655ad7a12f2ebb7c22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846806"
---
# <a name="design-the-infrastructure-persistence-layer"></a>Návrh vrstvy trvalosti infrastruktury

Součásti trvalosti dat poskytují přístup k datům hostovaným v rámci hranic mikroslužby (to znamená databáze mikroslužeb). Obsahují skutečné implementace komponent, jako jsou úložiště a [jednotky pracovních](https://martinfowler.com/eaaCatalog/unitOfWork.html) tříd, <xref:Microsoft.EntityFrameworkCore.DbContext> jako jsou vlastní entity Framework (EF) objekty. EF DbContext implementuje úložiště a vzory jednotky práce.

## <a name="the-repository-pattern"></a>Vzor úložiště

Repozitáře jsou třídy nebo součásti, které zapouzdřují logiku potřebnou pro přístup ke zdrojům dat. Centralizují běžné funkce přístupu k datům a poskytují lepší udržovatelnost a oddělují infrastrukturu nebo technologii používanou pro přístup k databázím z vrstvy modelu domény. Pokud používáte objekt relační mapovač (ORM), jako je entity Framework, kód, který musí být implementován je zjednodušena, díky LINQ a silné psaní. To umožňuje zaměřit se na logiku trvalost dat spíše než na připojení k datům instalatérství.

Vzor úložiště je dobře zdokumentovaný způsob práce se zdrojem dat. V knize [Vzory architektury podnikových aplikací](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/)popisuje Martin Fowler repozitář takto:

> Úložiště provádí úkoly prostředníka mezi vrstvami modelu domény a mapováním dat, které funguje podobně jako sada objektů domény v paměti. Klientské objekty deklarativně vytvářet dotazy a odesílat je do úložišť pro odpovědi. Koncepčně úložiště zapouzdřuje sadu objektů uložených v databázi a operace, které lze provést na nich, poskytuje způsob, který je blíže k vrstvě trvalosti. Repozitáře také podporují účel jasného a jednosměrného oddělení závislosti mezi pracovní doménou a přidělováním nebo mapováním dat.

### <a name="define-one-repository-per-aggregate"></a>Definovat jedno úložiště na agregaci

Pro každý agregační nebo agregační kořenbyste měli vytvořit jednu třídu úložiště. V mikroslužbě založené na vzoru návrhu řízeného doménou (DDD) by jediným kanálem, který byste měli použít k aktualizaci databáze, by měly být repozitáře. Důvodem je, že mají vztah 1:1 s agregační kořen, který řídí agregační invariants a transakční konzistence. Je v pořádku dotazovat databáze prostřednictvím jiných kanálů (stejně jako můžete provést po cqrs přístup), protože dotazy nemění stav databáze. Transakční oblast (tj. aktualizace) však musí být vždy řízena úložišti a agregačními kořeny.

V podstatě úložiště umožňuje naplnit data v paměti, která pochází z databáze ve formě entit domény. Jakmile entity jsou v paměti, mohou být změněny a potom trvalé zpět do databáze prostřednictvím transakcí.

Jak již bylo uvedeno dříve, pokud používáte architekturu CQS/CQRS, počáteční dotazy jsou prováděny vedlejšími dotazy mimo model domény, prováděné jednoduchými příkazy SQL pomocí Dapper. Tento přístup je mnohem flexibilnější než úložiště, protože můžete dotazovat a připojit všechny tabulky, které potřebujete, a tyto dotazy nejsou omezeny pravidly z agregací. Tato data přejdou do prezentační vrstvy nebo klientské aplikace.

Pokud uživatel provede změny, data, která mají být aktualizována, pocházejí z klientské aplikace nebo prezentační vrstvy do aplikační vrstvy (například služby webového rozhraní API). Když obdržíte příkaz v obslužné rutině příkazu, můžete použít úložiště k získání dat, která chcete aktualizovat z databáze. Aktualizujete jej v paměti s daty předanými pomocí příkazů a potom přidáte nebo aktualizujete data (entity domény) v databázi prostřednictvím transakce.

Je důležité znovu zdůraznit, že byste měli definovat pouze jedno úložiště pro každý kořenový adresář agregace, jak je znázorněno na obrázku 7-17. Chcete-li dosáhnout cíle agregační kořen zachovat transakční konzistenci mezi všechny objekty v rámci agregace, nikdy byste neměli vytvářet úložiště pro každou tabulku v databázi.

![Diagram znázorňující vztahy domény a jiné infrastruktury.](./media/infrastructure-persistence-layer-design/repository-aggregate-database-table-relationships.png)

**Obrázek 7-17**. Vztah mezi úložišti, agregacemi a databázovými tabulkami

Výše uvedený diagram znázorňuje vztahy mezi vrstvami domény a infrastruktury: Agregace kupujícího závisí na iBuyerRepository a Agregaci pořadí závisí na rozhraních IOrderRepository, tato rozhraní jsou implementována ve vrstvě infrastruktury podle odpovídající úložiště, které závisí na UnitOfWork, také implementována tam, že přistupuje k tabulkám v datové vrstvě.

### <a name="enforce-one-aggregate-root-per-repository"></a>Vynucení jednoho agregačního kořenového adresáře na úložiště

Může být užitečné implementovat návrh úložiště takovým způsobem, že vynucuje pravidlo, že pouze agregační kořeny by měly mít úložiště. Můžete vytvořit obecný nebo základní typ úložiště, který omezuje typ entit, se `IAggregateRoot` kterými pracuje, aby bylo zajištěno, že mají rozhraní značky.

Proto každá třída úložiště implementovaná ve vrstvě infrastruktury implementuje vlastní smlouvu nebo rozhraní, jak je znázorněno v následujícím kódu:

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

Lepší způsob, jak mít kód vynutit konvence, které každé úložiště souvisí s jeden agregace je implementovat obecný typ úložiště. Tímto způsobem je explicitní, že používáte úložiště k cílení na konkrétní agregaci. To lze snadno provést implementací obecného `IRepository` základního rozhraní, jako v následujícím kódu:

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Vzor úložiště usnadňuje testování aplikační logiky

Vzor úložiště umožňuje snadno otestovat aplikaci pomocí testování částí. Nezapomeňte, že testy částí pouze otestovat váš kód, nikoli infrastruktury, takže abstrakce úložiště usnadnit dosažení tohoto cíle.

Jak je uvedeno v předchozí části, doporučujeme definovat a umístit rozhraní úložiště do vrstvy modelu domény, aby aplikační vrstva, jako je mikroslužba webového rozhraní API, nezávisela přímo na vrstvě infrastruktury, do které jste implementovali třídy skutečného úložiště. Tímto způsobem a pomocí vkládání závislostí v řadičích webového rozhraní API můžete implementovat mock repozitáře, které vracejí falešná data namísto dat z databáze. Tento přístup oddělený umožňuje vytvářet a spouštět testy částí, které zaměřují logiku vaší aplikace bez nutnosti připojení k databázi.

Připojení k databázím může selhat a co je důležitější, spuštění stovky testů proti databázi je špatné ze dvou důvodů. Za prvé, to může trvat dlouhou dobu, protože velký počet testů. Za druhé, záznamy databáze může změnit a ovlivnit výsledky testů tak, aby nemusí být konzistentní. Testování proti databázi není testování částí, ale test integrace. Měli byste mít mnoho testů částí spuštěna rychle, ale méně testů integrace proti databázím.

Pokud jde o oddělení obavy pro testování částí, vaše logika pracuje na entity domény v paměti. Předpokládá, že třída úložiště je dodala. Jakmile vaše logika upraví entity domény, předpokládá, že třída úložiště je bude správně ukládat. Důležitým bodem je zde vytvořit testy částí proti modelu domény a jeho logiky domény. Agregační kořeny jsou hlavní hranice konzistence v DDD.

Úložiště implementovaná v eShopOnContainers spoléhají na implementaci EF Core DbContext vzoru úložiště a jednotky práce pomocí jeho sledování změn, takže tuto funkci neduplikují.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Rozdíl mezi vzorem úložiště a starším vzorem třídy přístupu k datům (třída DAL)

Objekt pro přístup k datům přímo provádí operace přístupu k datům a trvalosti proti úložišti. Úložiště označí data operacemi, které chcete provést v paměti jednotky pracovního objektu <xref:Microsoft.EntityFrameworkCore.DbContext> (jako v EF při použití třídy), ale tyto aktualizace nejsou prováděny okamžitě do databáze.

Jednotka práce se označuje jako jedna transakce, která zahrnuje více operací vložení, aktualizace nebo odstranění. Jednoduše řečeno, to znamená, že pro konkrétní akci uživatele, jako je například registrace na webu, jsou všechny operace vložení, aktualizace a odstranění zpracovány v jedné transakci. To je efektivnější než zpracování více databázových transakcí v chattier způsobem.

Tyto více operací trvalosti jsou prováděny později v jedné akci, když váš kód z aplikační vrstvy příkazy. Rozhodnutí o použití změn v paměti na skutečné úložiště databáze je obvykle založena na [jednotce práce vzor](https://martinfowler.com/eaaCatalog/unitOfWork.html). V EF je vzor jednotky práce <xref:Microsoft.EntityFrameworkCore.DbContext>implementován jako .

V mnoha případech tento vzor nebo způsob použití operací proti úložišti může zvýšit výkon aplikace a snížit možnost nekonzistence. Také snižuje blokování transakcí v databázových tabulkách, protože všechny zamýšlené operace jsou potvrzeny jako součást jedné transakce. To je efektivnější ve srovnání s prováděním mnoha izolovaných operací proti databázi. Proto vybrané ORM můžete optimalizovat provádění proti databázi seskupením několik akcí aktualizace v rámci stejné transakce, na rozdíl od mnoha malých a samostatných provádění transakcí.

### <a name="repositories-shouldnt-be-mandatory"></a>Repozitáře by neměly být povinné

Vlastní úložiště jsou užitečné z důvodů uvedených dříve a to je přístup pro řazení mikroslužeb v eShopOnContainers. Však není základní vzor implementovat v návrhu DDD nebo dokonce obecně .NET vývoj.

Například, Jimmy Bogard, při poskytování přímé zpětné vazby pro tuto příručku, řekl následující:

> Tohle bude asi moje největší zpětná vazba. Já opravdu nejsem fanoušek repozitářů, hlavně proto, že skrývají důležité detaily základního mechanismu perzistence. To je důvod, proč jsem jít na MediatR pro příkazy, taky. Mohu použít plnou sílu perzistence vrstvy, a tlačit všechny, že doména chování do mé souhrnné kořeny. Obvykle se nechci vysmívat svým repozitářům - stále potřebuji mít integrační test se skutečnou věcí. Chystáte CQRS znamenalo, že jsme neměli opravdu potřebu repozitářů nic víc.

Úložiště může být užitečné, ale nejsou důležité pro váš návrh DDD, tak, jak agregační vzor a bohatý model domény jsou. Proto použijte vzor úložiště nebo ne, jak uznáte za vhodné. V každém případě budete používat vzor úložiště při použití EF Core, i když v tomto případě úložiště pokrývá celou mikroslužbu nebo ohraničený kontext.

## <a name="additional-resources"></a>Další zdroje

### <a name="repository-pattern"></a>Vzor úložiště

- **Edward Hieatt a Rob mě. Vzor úložiště.** \
  <https://martinfowler.com/eaaCatalog/repository.html>

- **Vzor úložiště** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)>

- **Eric Evans. Návrh řízený doménou: Řešení složitosti v srdci softwaru.** (Kniha; obsahuje diskusi o vzoru úložiště) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="unit-of-work-pattern"></a>Jednotka pracovního vzoru

- **Martin Fowler. Jednotka pracovního vzoru.** \
  <https://martinfowler.com/eaaCatalog/unitOfWork.html>

- **Implementace úložiště a jednotky pracovních vzorů v ASP.NET aplikace MVC** \
  <https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

>[!div class="step-by-step"]
>[Předchozí](domain-events-design-implementation.md)
>[další](infrastructure-persistence-layer-implemenation-entity-framework-core.md)

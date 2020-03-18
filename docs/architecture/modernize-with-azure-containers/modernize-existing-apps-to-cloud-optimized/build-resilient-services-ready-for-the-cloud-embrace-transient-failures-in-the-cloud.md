---
title: Vytvářejte odolné služby připravené pro cloud. Zpracování přechodných selhání v cloudu
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Vytvářejte odolné služby připravené pro cloud. Zpracování přechodných selhání v cloudu
ms.date: 04/30/2018
ms.openlocfilehash: e516dc675ceb8def25c6d676bced0ea7f253b2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711252"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Vytváření odolných služeb připravených pro cloud: Zpracování přechodných selhání v cloudu

Odolnost proti chybám je schopnost zotavit se z chyb a nadále fungovat. Odolnost proti chybám není o předcházení chybám, ale o přijetí skutečnosti, že dojde k chybám, a následné reakci na ně způsobem, který zabraňuje výpadkům nebo ztrátě dat. Cílem odolnosti proti chybám je vrátit aplikaci do plně funkčního stavu po selhání.

Vaše aplikace je připravena pro cloud, když minimálně implementuje softwarový model odolnosti, nikoli hardwarový model. Vaše cloudová aplikace musí zahrnovat částečné chyby, které jistě nastanou. Navrhněte nebo částečně refaktorujte aplikaci, abyste dosáhli odolnosti proti chybám s očekávanými částečnými chybami. Měl by být navržen tak, aby se vypořádal s částečnými chybami, jako jsou přechodné výpadky sítě a uzly nebo selhání virtuálních počítačů v cloudu. I kontejnery přesouvány do jiného uzlu v rámci clusteru orchestrator může způsobit občasné krátké chyby v rámci aplikace.

## <a name="handling-partial-failure"></a>Zpracování částečného selhání

V cloudové aplikaci existuje stále přítomné riziko částečného selhání. Například jedna instance webu nebo kontejner může selhat nebo může být nedostupný nebo nereaguje na krátkou dobu. Nebo může dojít k selhání jednoho virtuálního aplikace nebo serveru.

Vzhledem k tomu, že klienti a služby jsou samostatné procesy, služba nemusí být schopen reagovat včas na požadavek klienta. Služba může být přetížena a reagovat pomalu na požadavky nebo nemusí být přístupná na krátkou dobu z důvodu problémů se sítí.

Zvažte například monolitickou aplikaci .NET, která přistupuje k databázi v Azure SQL Database. Pokud databáze Azure SQL nebo jiné služby třetích stran nereaguje na krátkou dobu (databáze Azure SQL může být přesunuta do jiného uzlu nebo serveru a nereaguje na několik sekund), když se uživatel pokusí provést jakoukoli akci, aplikace může dojít k chybě a v té min.

Podobný scénář může dojít v aplikaci, která spotřebovává služby HTTP. Síť nebo samotná služba nemusí být k dispozici v cloudu během krátké, přechodné selhání.

Odolná aplikace, jako je ta, která je znázorněna na obrázku 4-9, by měla implementovat techniky, jako je "opakování s exponenciálním zpětným vypnutím", aby aplikace měla příležitost zpracovat přechodná selhání prostředků. Měli byste také použít "jističe" ve vašich aplikacích. Jistič zastaví aplikace z pokusu o přístup k prostředku, když je to vlastně dlouhodobé selhání. Pomocí jističe, aplikace zabraňuje vyvolání odmítnutí služby pro sebe.

![Diagram částečné chyby zpracovány opakování s exponenciální backoff.](./media/retry-partial-failures.png)

**Obrázek 4-9.** Částečné chyby zpracované opakovanými pokusy s exponenciálním zpětným vypnutím

Tyto techniky můžete použít v prostředcích HTTP i v databázových prostředcích. Na obrázku 4-9 je aplikace založena na třívrstvé architektuře, takže potřebujete tyto techniky na úrovni služeb (HTTP) a na úrovni datové vrstvy (TCP). V monolitické aplikace, která používá pouze jednu vrstvu aplikace kromě databáze (žádné další služby nebo mikroslužeb), zpracování přechodných chyb na úrovni připojení databáze může být dost. V tomto scénáři je vyžadována pouze konkrétní konfigurace připojení databáze.

Při implementaci odolné komunikace, která přístup k databázi, v závislosti na verzi rozhraní .NET, které používáte, může být jednoduché (například [s Entity Framework 6 nebo novější](/ef/ef6/fundamentals/connection-resiliency/retry-logic). Je to jen otázka konfigurace připojení k databázi). Nebo budete muset použít další knihovny, jako [je přechodný blok aplikace zpracování chyb](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (pro starší verze rozhraní .NET) nebo dokonce implementovat vlastní knihovnu.

Při implementaci opakovaných pokusů http a jističů je doporučením pro rozhraní .NET použít [knihovnu Polly,](https://github.com/App-vNext/Polly) která cílí na rozhraní .NET Framework 4.0, .NET Framework 4.5 a .NET Standard 1.1, která zahrnuje podporu .NET Core.

Informace o tom, jak implementovat strategie pro zpracování částečné chyby v cloudu, naleznete v následujících odkazech.

### <a name="additional-resources"></a>Další zdroje

- **Implementace odolné komunikace pro zpracování částečného selhání**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **Odolnost k připojení rozhraní entity framework a logika opakování (verze 6 a novější)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **Blok aplikací zpracování přechodných chyb**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **Polly knihovna pro odolnou HTTP komunikaci**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[další](modernize-your-apps-with-monitoring-and-telemetry.md)

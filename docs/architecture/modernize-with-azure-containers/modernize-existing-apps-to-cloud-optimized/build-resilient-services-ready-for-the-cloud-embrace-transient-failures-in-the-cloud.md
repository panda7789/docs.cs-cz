---
title: Vytvářejte odolné služby připravené pro Cloud. Zpracování přechodných selhání v cloudu
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Vytvářejte odolné služby připravené pro Cloud. Zpracování přechodných selhání v cloudu
ms.date: 04/30/2018
ms.openlocfilehash: 5d25fb0d15ff7b9f04b9491454d1368e4aa7f593
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68677039"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Vytváření odolných služeb připravených pro cloud: Zpracování přechodných selhání v cloudu

Odolnost proti chybám je schopnost zotavení po selháních a nadále fungovat. Odolnost proti chybám nebrání, ale přijímá skutečnost, že dojde k selhání, a pak na ně reagovat způsobem, který brání výpadkům nebo ztrátě dat. Cílem odolnosti proti chybám je vrátit aplikaci do plně funkčního stavu po selhání.

Vaše aplikace je připravená na Cloud, pokud má přinejmenším za to, že implementuje softwarový model odolnosti, spíše než model založený na hardwaru. Vaše cloudová aplikace musí vycházet z částečně neúspěšných selhání. Navrhněte nebo částečně refaktorujte svoji aplikaci, aby se zajistila odolnost s očekávanými částečnými chybami. Měla by být navržená tak, aby se vypořádat s částečnými chybami, jako jsou přechodné výpadky sítě a uzly, nebo dojde k selhání virtuálních počítačů v cloudu. Dokonce i kontejnery, které se přesunou do jiného uzlu v rámci clusteru nástroje Orchestrator, můžou způsobit přerušované krátké chyby v rámci aplikace.

## <a name="handling-partial-failure"></a>Zpracování částečného selhání

V cloudové aplikaci existuje stále přítomné riziko částečného selhání. Například jedna instance webu nebo kontejner může selhat nebo může být nedostupná nebo nereaguje na krátkou dobu. Nebo může dojít k selhání jednoho virtuálního počítače nebo serveru.

Vzhledem k tomu, že klienti a služby jsou samostatné procesy, nemusí být služba schopná reagovat včas na požadavky klienta. Služba může být přetížena a reagovat pomalu na požadavky nebo nemusí být k dispozici po krátkou dobu kvůli problémům se sítí.

Zvažte například monolitické aplikaci .NET, která přistupuje k databázi v Azure SQL Database. Pokud Azure SQL Database nebo jakákoli jiná služba třetí strany nereaguje na krátkou dobu (může se stát, že se Azure SQL Database přesune na jiný uzel nebo server a nereaguje na několik sekund), když se uživatel pokusí provést jakoukoli akci, může aplikace selhat a zobrazit s výjimkou ve stejný okamžik.

Podobný scénář může nastat v aplikaci, která používá služby HTTP. Síť nebo samotná služba nemusí být v cloudu během krátkého přechodného selhání k dispozici.

Odolná aplikace jako ta, která je znázorněna na obrázku 4-9, by měla implementovat techniky, jako je "opakování s exponenciálním omezení rychlosti", aby aplikace mohla mít možnost zpracovávat přechodné chyby v prostředcích. V aplikacích byste také měli použít "okruhy okruhů". Přepínací modul okruhů zastaví aplikaci, aby se pokusil o přístup k prostředku, když je skutečně dlouhodobá chyba. Když použijete přerušení obvodu, aplikace zabrání tomu, aby provoking odepření služby.

![Částečné chyby zpracovávané opakováním exponenciálního omezení rychlostiu](./media/image9.png)

> **Obrázek 4-9.** Částečné chyby zpracovávané opakováním exponenciálního omezení rychlostiu

Tyto techniky můžete použít v prostředcích HTTP i v databázových prostředcích. Na obrázku 4-9 je aplikace založená na architektuře 3, takže tyto techniky budete potřebovat na úrovni služeb (HTTP) a na úrovni datové vrstvy (TCP). V aplikaci monolitické, která kromě databáze nástroje používá jenom jednu vrstvu aplikace (žádné další služby ani mikroslužby), může být dostatečné pro zpracování přechodných chyb na úrovni připojení databáze. V takovém scénáři je vyžadována pouze určitá konfigurace připojení k databázi.

Při implementaci odolné komunikace, která přistupuje k databázi, v závislosti na verzi rozhraní .NET, kterou používáte, může být jednoduchá (například [s Entity Framework 6 nebo novějším](/ef/ef6/fundamentals/connection-resiliency/retry-logic). Je to jenom ta konfigurace připojení k databázi). Nebo může být nutné použít další knihovny, jako je například [přechodný blok aplikace pro zpracování chyb](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (pro starší verze rozhraní .NET), nebo dokonce implementovat vlastní knihovnu.

Při implementaci opakování protokolu HTTP a přepínacích cyklů okruhu je doporučení pro .NET používat knihovnu [Polly](https://github.com/App-vNext/Polly) , která cílí na .NET Framework 4,0, .NET Framework 4,5 a .NET Standard 1,1, což zahrnuje podporu .NET Core.

Další informace o implementaci strategií pro zpracování částečných chyb v cloudu najdete v následujících odkazech.

### <a name="additional-resources"></a>Další zdroje

- **Implementace odolné komunikace pro zpracování částečného selhání**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **Entity Framework odolnost připojení a opakování logiky (verze 6 a novější)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **Blok aplikace pro zpracování přechodného selhání**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **Polly Library pro odolnou komunikaci HTTP**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)Další
>[](modernize-your-apps-with-monitoring-and-telemetry.md)

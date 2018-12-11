---
title: Vytváření odolných služeb připravených pro cloud. Zpracování přechodných selhání v cloudu
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Vytváření odolných služeb připravených pro cloud. Zpracování přechodných selhání v cloudu
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 16228321cc788b381603513213130415eb73a95c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128853"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Vytváření odolných služeb připravených pro cloud: Zpracování přechodných selhání v cloudu

Odolnost proti chybám je schopnost zotavení z chyb a nadále fungovat. Odolnost proti chybám není o předcházení chybám, ale přijímá skutečnost, že dojde k chybám a pak reagovat na ně způsobem, který zabraňuje výpadkům nebo ztrátě. Cílem odolnosti proti chybám je plně funkčního stavu aplikace po selhání.

Vaše aplikace je připravena pro cloud, když minimálně implementuje modelu založeného na softwaru odolnosti proti chybám, nikoli jako model založený na hardwaru. Vaše Cloudová aplikace musí využívat částečné chyby, ke kterým dojde jistě. Navrhujete nebo částečně Refaktorovat aplikace k zajištění odolnosti proti chybám s očekávané částečně neúspěšné. To by se měly navrhovat pro zvládnutí částečně neúspěšné, stejně jako přechodný síťový výpadků a uzly nebo virtuální počítače k chybám v cloudu. I kontejnery, který se přesouvá na jiný uzel v clusteru služby orchestrator může způsobit krátkodobých krátká selhání v rámci aplikace.

## <a name="handling-partial-failure"></a>Zpracování částečného selhání

V aplikaci založené na cloudu je všudypřítomnou riziko částečného selhání. Například instanci jednoho webu nebo kontejner může selhat nebo může být k dispozici nebo neodpovídá na krátkou dobu. Nebo jeden virtuální počítač nebo server, mohou selhat.

Protože samostatné procesy jsou klientů a služeb, nemusí služba včas reagovat na žádosti klienta. Službě mohou být přetížená a pomalé reakce na žádosti, nebo nemusí být dostupná pro krátkého formátu času z důvodu problémů se sítí.

Představte si třeba monolitické aplikace .NET, který přistupuje k databázi ve službě Azure SQL Database. Pokud je databáze Azure SQL nebo jakoukoli jinou službu třetí strany reagovat pro stručný čas (Azure SQL database může být přesunut do jiného uzlu nebo na server a nebudou reagovat na několik sekund), když se uživatel pokusí provést žádnou akci, může dojít k selhání aplikace a zobrazit w výjimku ve stejnou chvíli.

Informace o podobném scénáři se může stát v aplikaci, která využívá služby HTTP. Síť nebo službu samotnou nemusí být k dispozici v cloudu během krátké, přechodná selhání.

Odolné aplikace zobrazený obrázek 4 – 9, by měly implementovat postupů, jako jsou "opakování pomocí exponenciálního omezení rychlosti" poskytnout příležitosti pro zpracování přechodných selhání v prostředcích aplikace. "Jističe" také měli použít ve svých aplikacích. Jističe přestane aplikace v pokusu o přístup k prostředku, když je ve skutečnosti dlouhodobé selhání. Aplikace s použitím jističe, se vyhnete webinářem útok DoS sám na sebe.

![Částečně neúspěšné zpracovat opakování pomocí exponenciálního omezení rychlosti](./media/image9.png)

> **Obrázek 4 – 9.** Částečně neúspěšné zpracovat opakování pomocí exponenciálního omezení rychlosti

Tyto postupy můžete použít zdroje HTTP a databázových prostředků. Obrázek 4 – 9 aplikace jsou založené na 3vrstvou architekturu, je třeba těchto technik na úrovni služeb (HTTP) a na úrovni datové vrstvy (TCP). V monolitické aplikaci, která používá jenom na úrovni aplikace s jedním kromě databáze (Další služby ani mikroslužeb) zpracování přechodných chyb na úrovni databáze, připojení může být dostačující. V této situaci se vyžaduje jenom konkrétní konfiguraci připojení k databázi.

Při implementaci odolných komunikaci, kterou si přístup k databázi, v závislosti na verzi technologie .NET, které používáte, může být jednoduché (například [s Entity Framework 6 nebo novější](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx), je jenom na vás konfigurace připojení k databázi). Nebo možná budete muset používat další knihovny se podobně jako [přechodné Fault Handling Application Block](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (pro starší verze rozhraní .NET), nebo dokonce implementují vlastní knihovny.

Při provádění opakování HTTP a jističe, doporučení pro .NET je použít [Polly](https://github.com/App-vNext/Polly) knihovny, která cílí na rozhraní .NET Framework 4.0, .NET Framework 4.5 a .NET Standard 1.1, včetně podpory .NET Core.

Zjistěte, jak implementovat strategie pro zpracování částečného selhání v cloudu, najdete v následujících odkazech.

### <a name="additional-resources"></a>Další zdroje

-   **Implementace odolných komunikace pro zpracování částečného selhání**

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](../../microservices-architecture/implement-resilient-applications/partial-failure-strategies.md)

-   **Entity Framework odolnost proti chybám a zkuste to znovu logiku připojení (verze 6 a novější)**

    [https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)

-   **Blok aplikací zpracování přechodných chyb**

-   [https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx)

-   **Knihovnu Polly pro odolný komunikaci pomocí protokolu HTTP**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[další](modernize-your-apps-with-monitoring-and-telemetry.md)
---
title: Kandidátské aplikace pro cloudové nativní
description: Seznamte se s typy aplikací, které využívají nativní přístup z cloudu.
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 2087ef0c327a82419be95552293d1b56742b73c7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337435"
---
# <a name="candidate-apps-for-cloud-native"></a>Kandidátské aplikace pro cloudové nativní

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Podívejte se na aplikace v portfoliu. Kolik z nich splňuje podmínky pro nativní cloudovou architekturu? Všechny? Možná nějaké?

Když použijete analýzu nákladů a přínosů, je velmi pravděpodobné, že nebudete mít k dispozici Hefty cenové značky, která se vyžaduje pro cloudovou nativní podporu. Náklady na cloudový Native by daleko překročily obchodní hodnotu aplikace.

Jaký typ aplikace může být kandidátem na nativní Cloud?

- Velký strategický podnikový systém, který potřebuje neustále vyvíjet obchodní možnosti/funkce

- Aplikace, která vyžaduje vysokou rychlost vydání verze – s vysokou jistotou

- Systém, ve kterém musí jednotlivé funkce vydávat *bez* úplného opětovného nasazení celého systému

- Aplikace vyvinutá týmy s odbornými znalostmi různých technologických zásobníků

- Aplikace s komponentami, které se musí nezávisle škálovat

Pak jsou starší verze systémů. I když bychom chtěli vytvářet nové aplikace, často zodpovídáme za modernizaci starší verze úloh, které jsou pro firmu zásadní. V průběhu času může být starší verze aplikace rozdělená do mikroslužeb, kontejnerů a nakonec "navýšení" na nativní cloudovou architekturu.

### <a name="modernizing-legacy-apps"></a>Modernizaci starší verze aplikací

Bezplatná elektronická kniha Microsoftu [modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) poskytuje pokyny pro migraci místních úloh do cloudu. Obrázek 1-10 ukazuje, že pro modernizaci starší verze aplikací není k dispozici jedna strategie pro všechny velikosti.

![Strategie migrace starších verzí úloh](./media/strategies-for-migrating-legacy-workloads.png)

**Obrázek 1-10**. Strategie migrace starších verzí úloh

Monolitické aplikace, které jsou nepostradatelné, přináší z provozu rychlou migraci ([připravenou pro cloudovou infrastrukturu](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)). V tomto případě se místní úloha znovu hostuje na cloudový virtuální počítač beze změn. Tento přístup používá [model IaaS (infrastruktura jako služba)](https://azure.microsoft.com/overview/what-is-iaas/). Azure obsahuje několik nástrojů, jako je například ([Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)a [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/)), aby bylo možné tento přesun usnadnit. I když tato strategie může přinést určitou úsporu nákladů, takové aplikace se většinou nemusely rozdávat a využívat výhody cloud computingu.

Monolitické aplikace, které jsou důležité pro obchodní často, využívají výhod vylepšené migrace za provozu a posunutí (*optimalizované pro Cloud*). Tento přístup zahrnuje optimalizace nasazení, které umožňují klíčovou službu Cloud Services – bez změny základní architektury aplikace. Například můžete aplikaci [kontejnerizace](https://docs.microsoft.com/virtualization/windowscontainers/about/) a nasadit ji na produkt Orchestrator, jako je třeba [Služba Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/), která je popsána dále v této příručce. V cloudu může aplikace využívat jiné cloudové služby, jako jsou databáze, fronty zpráv, monitorování a distribuované ukládání do mezipaměti.

Aplikace monolitické, které provádějí strategické podnikové funkce, můžou nejlépe těžit z *cloudového nativního* přístupu, který je předmětem této knihy. Tento přístup poskytuje flexibilitu a rychlost. Ale přináší náklady na replatformování, rearchitekturu a přepis kódu.

Pokud se vy a váš tým domníváte, že se jedná o cloudový nativní přístup, je vhodné, abyste s vaší organizací behooves racionalizovat rozhodnutí. Jak přesně se jedná o obchodní problém, který vyřeší cloudový nativní přístup? Jak by to bylo v souladu s podnikovými požadavky?

- Rychlé verze funkcí s větší jistotou?

- Jemně odstupňovaná škálovatelnost – efektivnější využití prostředků?

- Zlepšila se odolnost systému?

- Vylepšený výkon systému?

- Máte lepší přehled o operacích?

- Vývojové platformy a úložiště dat pro vývoj v Blendu k dosažení nejlepšího nástroje pro úlohu?

- Budoucí investice do aplikace pro kontrolu pravopisu?

Správná strategie migrace závisí na prioritách organizace a na systémech, které cílíte. V mnoha případech může být výhodnější zvýšit náklady na Cloud – optimalizuje aplikaci monolitické nebo do N-vrstvé aplikace přidat hrubě odstupňované služby. V těchto případech můžete plně využívat možnosti cloudového PaaSu, jako jsou ty, které nabízí Azure App Service.

## <a name="summary"></a>Přehled

V této kapitole jsme představili výpočetní prostředí pro Cloud. Poskytli jsme definici společně s klíčovými možnostmi, které zajišťují cloudovou nativní aplikaci. Prohlédli jsme se na typech aplikací, které by mohly tuto investici a úsilí zdůvodnit.

V úvodu na pozadí jsme teď podrobněi mnohem podrobnější pohled na Cloud Native.

### <a name="references"></a>Reference

- [Cloud Native Computing Foundation](https://www.cncf.io/)

- [Mikroslužby .NET: architektura pro kontejnerové aplikace .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [Nativní vzory cloudu podle Cornelia Davis](https://www.manning.com/books/cloud-native-patterns)

- [Mimo aplikaci dvanáct-Factor](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [Co je infrastruktura jako kód](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [Micro Deploys v Uber Engineering: každodenní nasazení s jistotou](https://eng.uber.com/micro-deploy/)

- [Jak Netflix nasazuje kód](https://www.infoq.com/news/2013/06/netflix/)

- [Přetížení ovládacího prvku pro škálování mikroslužeb WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[Předchozí](definition.md)
>[Další](introduce-eshoponcontainers-reference-app.md)

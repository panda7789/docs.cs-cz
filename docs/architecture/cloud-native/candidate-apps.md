---
title: Kandidátské aplikace pro nativní cloud
description: Zjistěte, které typy aplikací využívají přístup založený na cloudu
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 8e58f5bd3aa0a4503ea73ab454e42e863eb0bb5d
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805613"
---
# <a name="candidate-apps-for-cloud-native"></a>Kandidátské aplikace pro nativní cloud

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Podívejte se na aplikace ve svém portfoliu. Kolik z nich má nárok na architekturu nativní pro cloud? Všechny? Možná nějaké?

Použití analýzy nákladů a přínosů je velká šance, že většina z nich nebude podporovat statnou cenovku, která musí být nativní v cloudu. Náklady na cloud nativní by daleko překročit obchodní hodnotu aplikace.

Jaký typ aplikace může být kandidátem pro nativní cloud?

- Velký, strategický podnikový systém, který potřebuje neustále vyvíjet obchodní schopnosti/ funkce

- Aplikace, která vyžaduje vysokou rychlost uvolňování – s vysokou jistotou

- Systém, ve kterém se musí jednotlivé funkce uvolnit *bez* úplného přerozdělení celého systému

- Aplikace vyvinutá týmy s odbornými znalostmi v různých technologických hromádkách

- Aplikace s komponentami, které musí škálovat nezávisle

Pak jsou tu starší systémy. I když bychom všichni chtěli vytvářet nové aplikace, jsme často zodpovědní za modernizaci starších úloh, které jsou pro firmu klíčové. V průběhu času může být starší aplikace rozložena na mikroslužby, kontejnerizovaná a nakonec "replatformed" do architektury nativní pro cloud.

### <a name="modernizing-legacy-apps"></a>Modernizace starších aplikací

Bezplatná e-kniha Microsoft [modernizuje stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) poskytuje pokyny pro migraci místních úloh do cloudu. Obrázek 1-10 ukazuje, že neexistuje jediná, jedna velikost pro všechny strategie pro modernizaci starších aplikací.

![Strategie migrace starších úloh](./media/strategies-for-migrating-legacy-workloads.png)

**Obrázek 1-10**. Strategie migrace starších úloh

Monolitické aplikace, které nejsou kritické, z velké části těží z rychlé migrace výtahu a posunu[(Cloud Infrastructure-Ready).](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md) Tady je místní úloha rehosted na virtuální počítač na základě cloudu, beze změn. Tento přístup používá [model IaaS (Infrastruktura jako služba).](https://azure.microsoft.com/overview/what-is-iaas/) Azure obsahuje několik nástrojů, jako je [Migrace Azure](https://azure.microsoft.com/services/azure-migrate/), Azure [Site Recovery](https://azure.microsoft.com/services/site-recovery/)a Azure Database [Migration Service,](https://azure.microsoft.com/campaigns/database-migration/) aby takový přesun jednodušší. I když tato strategie může přinést určité úspory nákladů, tyto aplikace obvykle nebyly navrženy tak, aby odemkly a využily výhod cloud computingu.

Monolitické aplikace, které jsou pro firmu kritické, mají často prospěch z rozšířené migrace výtahu a posunu *(optimalizovaná pro cloud).* Tento přístup zahrnuje optimalizace nasazení, které umožňují klíčové cloudové služby – beze změny základní architektury aplikace. Můžete například [kontejnerizovat aplikaci](https://docs.microsoft.com/virtualization/windowscontainers/about/) a nasadit ji do orchestrátoru kontejneru, jako je [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), popsané dále v této knize. Jakmile je aplikace v cloudu, může využívat další cloudové služby, jako jsou databáze, fronty zpráv, monitorování a distribuované ukládání do mezipaměti.

Nakonec monolitické aplikace, které vykonávají strategické podnikové funkce, mohou nejlépe těžit z přístupu *nativního pro cloud,* který je předmětem této knihy. Tento přístup poskytuje agility a rychlost. Ale to přijde za cenu replatforming, rearchitecting, a přepisování kódu.

Pokud vy a váš tým věří, že přístup nativní pro cloud je vhodný, slábne soudůvodit rozhodnutí s vaší organizací. Co přesně je obchodní problém, který vyřeší přístup nativní pro cloud? Jak by to bylo v souladu s obchodními potřebami?

- Rychlé uvolnění funkcí se zvýšenou důvěrou?

- Jemně odstupňovaná škálovatelnost - efektivnější využití zdrojů?

- Vylepšená odolnost systému?

- Zlepšený výkon systému?

- Větší přehled o operacích?

- Blend vývojové platformy a úložiště dat, aby se dospělo k nejlepšímu nástroji pro práci?

- Investice do aplikací, které obnaží budoucnost?

Správná strategie migrace závisí na prioritách organizace a systémech, na které cílíte. Pro mnohé může být nákladově efektivnější optimalizovat cloud monolitickou aplikaci nebo přidat hrubé odstupňované služby do aplikace N-Tier. V těchto případech můžete stále plně využívat cloudové paas funkce, jako jsou ty, které nabízí Azure App Service.

## <a name="summary"></a>Souhrn

V této kapitole jsme zavedli cloud-nativní výpočetní techniky. Poskytli jsme definici spolu s klíčovými funkcemi, které řídí aplikaci nativní pro cloud. Podívali jsme se na typy aplikací, které by mohly ospravedlnit tuto investici a úsilí.

Se zavedením za sebou se nyní ponoříme do mnohem podrobnějšího pohledu na nativní cloud.

### <a name="references"></a>Odkazy

- [Nadace cloudnative computingu](https://www.cncf.io/)

- [.NET Microservices: Architektura pro kontejnerizované aplikace .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Modernizace stávajících aplikací .NET pomocí cloudu Azure a kontejnerů s Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [Cloud Nativní vzory od Cornelia Davis](https://www.manning.com/books/cloud-native-patterns)

- [Kromě dvanáctifaktorové aplikace](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [Co je infrastruktura jako kód](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [Micro Deploy společnosti Uber Engineering: Nasazení denně s důvěrou](https://eng.uber.com/micro-deploy/)

- [Jak Netflix nasazuje kód](https://www.infoq.com/news/2013/06/netflix/)

- [Řízení přetížení pro škálování WeChat Microservices](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[Předchozí](definition.md)
>[další](introduce-eshoponcontainers-reference-app.md)

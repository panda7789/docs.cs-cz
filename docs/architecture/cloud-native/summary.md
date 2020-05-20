---
title: Souhrn
description: Shrnutí klíčových závěrů z architekta nativních cloudových aplikací .NET pro Azure – příručka a elektronická kniha.
ms.date: 05/13/2020
ms.openlocfilehash: b1a195c0c081565c57f5aac2e234411bb904ca08
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613652"
---
# <a name="summary"></a>Souhrn

Tady jsou důležité závěry z tohoto průvodce:

- **Cloud-Native** se týká návrhu moderních aplikací, které přijišťují rychlou změnu, velký rozsah a odolnost, v moderních a dynamických prostředích, jako jsou veřejné, privátní a hybridní cloudy.

- ** [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF)** je nepřehledný open source konsorcium nad 300 hlavními společnostmi. Zodpovídá za to, aby se nahrálo využívání cloudového nativního výpočetního prostředí napříč technologiemi a cloudových zásobníků.

- **Pokyny pro CNCF** doporučují, aby nativní aplikace cloudu Zay šest důležitých pilířů, jak je znázorněno na obrázku 11-1:

  ![Základní pilíře pro Cloud – nativní](./media/cloud-native-foundational-pillars.png)

  **Obrázek 11-1**. Základní pilíře pro Cloud – nativní

- Tyto pilíře nativní pro Cloud zahrnují:
  - Cloud a jeho základní model služby
  - Moderní principy návrhu
  - Mikroslužby
  - Rozbalení a orchestrace kontejnerů
  - Cloudové služby zálohování, jako jsou databáze a zprostředkovatelé zpráv
  - Automatizace, včetně infrastruktury jako kódu a nasazení kódu

- **Kubernetes** je hostující prostředí, které je vhodné pro většinu aplikací nativních pro Cloud. Menší jednoduché služby se někdy hostují na platformách bez serveru, jako je Azure Functions. Mezi mnoha klíčovými funkcemi automatizace nabízí obě prostředí automatické škálování pro zpracování kolísání objemu úloh.

- **Komunikace se službou** se při vytváření cloudové nativní aplikace stala významným rozhodnutím pro návrh. Aplikace obvykle zpřístupňují bránu API pro správu klientské komunikace front-endu. Pak back-end mikroslužby usilují o komunikaci s ostatními implementacemi vzorů asynchronní komunikace, pokud je to možné.

- **gRPC** je moderní, vysoce výkonné rozhraní, které vyvíjí stáří protokolu RPC (Remote Procedure Call). Nativní aplikace v cloudu často přibývají gRPC a zjednodušují zasílání zpráv mezi back-end službami. gRPC používá pro svůj transportní protokol HTTP/2. Může to být až 8x rychlejší než serializace JSON s velikostí zpráv 60-80% menší. gRPC je open source a spravuje je CNCF (Cloud Native Computing Foundation).

- **Distribuovaná data** jsou model, který je často implementován pomocí cloudových nativních aplikací. Aplikace oddělí obchodní funkce na malé nezávislé mikroslužby. Každá mikroslužba zapouzdřuje své vlastní závislosti, data a stav. Model klasického sdíleného databáze se vyvíjí do jedné z mnoha menších databází, z nichž každý je zarovnaný k mikroslužbám. Když se kouř nevymaže, ukážeme vám návrh, který zveřejňuje `database-per-microservice` model.

- **Žádné databáze SQL** neodkazují na vysoce výkonná a nerelační úložiště dat. Jsou v Excelu ve vlastnostech snadného použití, škálovatelnosti, odolnosti a dostupnosti. Vysoce výkonné služby, které vyžadují dobu odezvy sub Second NoSQL úložiště dat. Šíření NoSQL technologií pro distribuované cloudové systémy nelze přestavovat.

- **NewSQL** je rozvíjející se Databázová technologie, která kombinuje distribuovanou škálovatelnost NOSQL a kyselé záruky relační databáze. Databáze NewSQL cílí na podnikové systémy, které musí zpracovávat velké objemy dat napříč distribuovanými prostředími, a to s využitím úplných transakčních a KYSELých předpisů. Cloud Native Computing Foundation (CNCF) obsahuje několik databázových projektů NewSQL.

- **Odolnost** proti chybám je schopnost systému reagovat na selhání a pořád zůstává funkční. Nativní systémy v cloudu zadávají distribuovanou architekturu, ve které je selhání nevyhnutelné. Aplikace musí být vytvořené tak, aby reagovaly na neúspěšné a rychle se vracely do plně funkčního stavu.

- **Sítě** jsou konfigurovatelnou vrstvou infrastruktury s integrovanými funkcemi pro zpracování komunikace služby a dalších výzev k vzájemnému vyjmutí. Odpojí zodpovědnost mezi jednotlivými obchodními kódy. Tyto odpovědnosti se přesunou na proxy služby. Označované jako `Sidecar pattern` , proxy server se nasadí do samostatného procesu, který poskytuje izolaci z vašeho podnikového kódu.

- **Pozorování** je klíčovým aspektem pro cloudové nativní aplikace. Jelikož jsou služby distribuované napříč clusterem uzlů, centralizované protokolování, monitorování a výstrahy se stanou povinnými. Azure Monitor je kolekce cloudových nástrojů navržených tak, aby poskytovaly přehled o stavu systému.

- **Infrastruktura jako kód** je široce přijatá praxe, která automatizuje zřizování platforem. Vaše infrastruktura a nasazení jsou automatizované, konzistentní a opakované. Nástroje jako Azure Resource Manager, Terraformu a Azure CLI umožňují deklarativní skriptování cloudové infrastruktury, kterou požadujete.

- **Automatizace kódu** je požadavek pro aplikace nativní pro Cloud. Moderní systémy CI/CD můžou splnit tento princip. Poskytují samostatné kroky sestavení a nasazení, které vám pomohou zajistit konzistentní a kvalitní kód. Fáze sestavení transformuje kód do binárního artefaktu. Fáze vydání vybere binární artefakt, použije konfiguraci externího prostředí a nasadí ho do zadaného prostředí. Azure DevOps a GitHub jsou plnohodnotná DevOps prostředí.

>[!div class="step-by-step"]
>[Předchozí](application-bundles.md)

---
title: Schémata komunikace nativní pro cloud
description: Další informace o komunikaci s klíčovou službou v cloudových nativních aplikacích
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 3d678df44b5fef68427846e59f446b7408795625
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614211"
---
# <a name="cloud-native-communication-patterns"></a>Schémata komunikace nativní pro cloud

Při sestavování nativního cloudového systému se komunikace stala významným rozhodnutím o návrhu. Jak klientská aplikace front-endu komunikuje s back-end mikroslužbami? Jak vzájemně komunikují mikroslužby back-end? Jaké jsou zásady, vzory a osvědčené postupy, které je potřeba vzít v úvahu při implementaci komunikace v cloudových nativních aplikacích?

## <a name="communication-considerations"></a>Otázky komunikace

V aplikaci monolitické je komunikace jednoduchá. Kódové moduly se provádějí společně ve stejném spustitelném prostoru (procesu) na serveru. Tento přístup může mít vliv na výkon, protože všechno běží dohromady ve sdílené paměti, ale má za následek velmi složitý kód, který se může obtížně udržovat, vyvíjet a škálovat.

Cloudové nativní systémy implementují architekturu založenou na mikroslužbách s mnoha malými nezávislými mikroslužbami. Každá mikroslužba se spouští v samostatném procesu a obvykle se spouští uvnitř kontejneru, který je nasazený do *clusteru*.

Cluster seskupuje fond virtuálních počítačů dohromady, aby bylo možné vytvořit vysoce dostupné prostředí. Spravují se nástrojem orchestrace, který zodpovídá za nasazení a správu kontejnerových mikroslužeb. Obrázek 4-1 ukazuje cluster [Kubernetes](https://kubernetes.io) nasazený do cloudu Azure s plně spravovanými [službami Azure Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes).

![Cluster Kubernetes v Azure](./media/kubernetes-cluster-in-azure.png)

**Obrázek 4-1**. Cluster Kubernetes v Azure

Mezi clustery komunikuje mikroslužby vzájemně prostřednictvím rozhraní API a technologií zasílání zpráv.

I když poskytují spoustu výhod, mikroslužby nejsou bezplatné na oběd. Volání místní metody v procesu mezi komponentami jsou nyní nahrazena síťovými voláními. Každá mikroslužba musí komunikovat přes síťový protokol, což zvyšuje složitost vašeho systému:

- Při zahlcení sítě, latenci a přechodných chybách se jedná o konstantní problém.

- Odolnost proti chybám (tj. opakování neúspěšných požadavků) je zásadní.

- Některá volání musí být [idempotentní](https://www.restapitutorial.com/lessons/idempotency.html) , aby zachovala konzistentní stav.

- Každá mikroslužba musí ověřovat a autorizovat volání.

- Každou zprávu je nutné serializovat a pak deserializovat – což může být nákladné.

- Šifrování a dešifrování zpráv bude důležité.

Mikroslužby Book [.NET: architektura pro kontejnerové aplikace .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook), která je dostupná zdarma od Microsoftu, poskytuje podrobné pokrytí způsobů komunikace pro aplikace mikroslužeb. V této kapitole poskytujeme podrobný přehled těchto vzorů spolu s možnostmi implementace dostupnými v cloudu Azure.

V této kapitole budeme řešit komunikaci mezi front-end aplikacemi a back-endové mikroslužbami. Pak se podíváme na back-endové mikroslužby, které navzájem komunikují. Prozkoumáme komunikační technologii gRPC a. Nakonec podíváme se na nové inovativní způsoby komunikace pomocí technologie sítě služby. Ukážeme vám také, jak Cloud Azure poskytuje různé druhy *služeb* , které umožňují podporovat komunikaci v cloudu.

>[!div class="step-by-step"]
>[Předchozí](other-deployment-options.md) 
> [Další](front-end-communication.md)

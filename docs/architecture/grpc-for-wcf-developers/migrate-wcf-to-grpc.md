---
title: Migrace řešení WCF do gRPC-gRPC pro vývojáře WCF
description: Postup migrace různých typů služby WCF na ekvivalent v gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 33823d20e1593323a03da12981c5a4534c4d491a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971773"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a>Migrace řešení WCF do gRPC

V této kapitole se dozvíte, jak pracovat s projekty ASP.NET Core 3,0 gRPC a předvádíme migraci různých typů služeb WCF na gRPC ekvivalent:

- Vytvořte projekt ASP.NET Core 3,0 gRPC.
- Jednoduché operace požadavek-odpověď na gRPC unárního RPC.
- Jednosměrné operace pro gRPC streamování klientů RPC
- Plně duplexní služby pro gRPC obousměrného streamování RPC.

Existuje také porovnání používání služby streamování a opakujících se polí pro vracení datových sad a použití klientských knihoven na konci kapitoly.

Ukázková aplikace WCF je minimální zástupná procedura sady burzovních obchodních služeb s použitím open source knihovny kontejnerů IoC (inverze Control) s názvem *Autofac* pro vkládání závislostí. Zahrnuje tři služby, jeden pro každý typ služby WCF. V následujících částech jsou popsány podrobné informace o službách. Řešení je možné stáhnout z příkazu [dotnet-Architecture/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) na GitHubu. Služby používají falešná data k minimalizaci externích závislostí.

Ukázky zahrnují implementace WCF a gRPC každé služby.

>[!div class="step-by-step"]
>[Předchozí](ws-protocols.md)
>[Další](create-project.md)

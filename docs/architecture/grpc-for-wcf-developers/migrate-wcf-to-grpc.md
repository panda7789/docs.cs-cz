---
title: Migrace řešení WCF do gRPC-gRPC pro vývojáře WCF
description: Postup migrace různých typů služeb WCF na ekvivalent v gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 12e724ab46a33547d352da7a604a5a994e617bc2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628511"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a>Migrace řešení WCF do gRPC

Tato kapitola popisuje, jak pracovat s projekty ASP.NET Core 3,0 gRPC a předvést migraci různých typů služeb Windows Communication Foundation (WCF) na gRPC ekvivalent:

- Vytvořte projekt ASP.NET Core 3,0 gRPC.
- Jednoduché operace požadavek-odpověď na gRPC unárního RPC.
- Jednosměrné operace pro gRPC streamování klientů RPC
- Plně duplexní služby pro gRPC obousměrného streamování RPC.

Existuje také porovnání používání služby streamování a opakujících se polí pro vrácení datových sad a existuje diskuze o použití klientských knihoven na konci kapitoly.

Ukázková aplikace WCF je minimální zástupná procedura sady burzovních obchodních služeb. Pro vkládání závislostí používá knihovnu kontejnerů Open Source Inversion Control (IoC) s názvem Autofac. Zahrnuje tři služby, jeden pro každý typ služby WCF. V následujících částech jsou popsány podrobné informace o službách. Řešení můžete stáhnout z příkazu [dotnet-Architecture/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) na GitHubu. Služby používají falešná data k minimalizaci externích závislostí.

Ukázky zahrnují implementace WCF a gRPC každé služby.

>[!div class="step-by-step"]
>[Předchozí](ws-protocols.md)
>[Další](create-project.md)

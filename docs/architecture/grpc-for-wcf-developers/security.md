---
title: Zabezpečení v gRPC aplikacích - gRPC pro vývojáře WCF
description: Přehled ověřování a autorizace volání a kanálů v gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 70cbf441bbc1b299b997f7d1f02bcd2bf7fde60c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147812"
---
# <a name="security-in-grpc-applications"></a>Zabezpečení v aplikacích gRPC

V každém reálném scénáři je zabezpečení aplikací a služeb nezbytné. Bezpečnost zahrnuje tři klíčové oblasti:

* Šifrování síťového provozu, aby se zabránilo škodlivým hackerům v jeho zachycení.
* Ověřování klientů a serverů za účelem vytvoření identity a důvěryhodnosti.
* Autorizace klientů k řízení přístupu k systémům a použití oprávnění na základě identity.

> [!NOTE]
> *Ověřování* se týká zjištění identity klienta nebo serveru. *Autorizace* se týká určení, zda má klient oprávnění k přístupu k prostředku nebo k vydání příkazu.

Tato kapitola se bude týkat zařízení pro ověřování a autorizaci v gRPC pro ASP.NET Core. Bude také diskutovat o zabezpečení sítě prostřednictvím šifrovaných připojení TLS.

## <a name="wcf-authentication-and-authorization"></a>Ověřování a autorizace WCF

V systému Windows Communication Foundation (WCF) ověřování a autorizace byly zpracovány různými způsoby, v závislosti na přenosy a vazby používané. WCF podporovalrůzné standardy\* zabezpečení WS. Podporovala také ověřování systému Windows pro služby HTTP spuštěné ve službě IIS nebo nettcp služby mezi systémy Windows.

## <a name="grpc-authentication-and-authorization"></a>gRPC ověřování a autorizace

gRPC ověřování a autorizace funguje na dvou úrovních:

* Ověřování/autorizace na úrovni volání se obvykle zpracovává prostřednictvím tokenů, které jsou použity v metadatech při volání.
* Ověřování na úrovni kanálu používá klientský certifikát, který je použit na úrovni připojení. Může také obsahovat pověření pro ověřování/autorizaci na úrovni volání, která se použijí na každé volání v kanálu automaticky.

Můžete použít jeden nebo oba tyto mechanismy k zabezpečení služby.

ASP.NET Core implementace gRPC podporuje ověřování a autorizaci prostřednictvím většiny standardních ASP.NET core mechanismy:

- Ověření volání
  - Azure Active Directory
  - IdentityServer
  - JWT Žeton nosiče
  - OAuth 2.0
  - OpenID Connect
  - WS-Federation
- Ověřování kanálu
  - Klientský certifikát

Všechny metody ověřování volání jsou založeny na *tokenech*. Jediným skutečným rozdílem je, jak jsou generovány tokeny a knihovny, které se používají k ověření tokeny ve službě ASP.NET Core.

Další informace naleznete v článku [Ověřování a autorizace.](/aspnet/core/grpc/authn-and-authz)

> [!NOTE]
> Pokud používáte gRPC přes připojení HTTP/2 šifrované protokolem TLS, veškerý provoz mezi klienty a servery je šifrován, i když nepoužíváte ověřování na úrovni kanálu.

Tato kapitola ukáže, jak použít pověření volání a pověření kanálu pro službu gRPC. Také ukáže, jak používat pověření z klienta .NET Core gRPC k ověření se službou.

>[!div class="step-by-step"]
>[Předchozí](client-libraries.md)
>[další](call-credentials.md)

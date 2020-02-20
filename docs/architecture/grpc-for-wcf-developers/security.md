---
title: Zabezpečení v gRPC aplikacích – gRPC pro vývojáře WCF
description: Přehled ověřování volání a kanálu a autorizaci v gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: d5804ad5de4a834eb81b90fa1ea7a61969a0b42f
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503419"
---
# <a name="security-in-grpc-applications"></a>Zabezpečení v aplikacích gRPC

V jakémkoli scénáři reálného světa je zabezpečení aplikací a služeb zásadní. Zabezpečení pokrývá tři klíčové oblasti: 

* Šifrování síťového provozu, aby nedocházelo ke škodlivému hackerům v zachycení.
* Ověřování klientů a serverů k navázání identity a vztahu důvěryhodnosti.
* Autorizace klientů pro řízení přístupu k systémům a uplatnění oprávnění na základě identity.

> [!NOTE]
> *Ověřování* se týká vytvoření identity klienta nebo serveru. K určení toho, jestli má klient oprávnění pro přístup k prostředku nebo k vystavení příkazu, se jedná o *autorizaci* .

Tato kapitola se zabývá zařízeními pro ověřování a autorizaci v gRPC pro ASP.NET Core. Bude taky projednávat zabezpečení sítě prostřednictvím šifrovaných připojení TLS.

## <a name="wcf-authentication-and-authorization"></a>Ověřování a autorizace WCF

V Windows Communication Foundation (WCF) byly ověřování a autorizace zpracovávány různými způsoby v závislosti na používaných přenosech a vazbách. Služba WCF podporuje různé standardy zabezpečení WS-\*. Také podporuje ověřování systému Windows pro služby HTTP spuštěné ve službě IIS nebo NetTCP Services mezi systémy Windows.

## <a name="grpc-authentication-and-authorization"></a>ověřování a autorizace gRPC

ověřování a autorizace gRPC funguje na dvou úrovních:

* Ověřování/autorizace na úrovni volání je obvykle zpracovávána prostřednictvím tokenů, které jsou v metadatech při volání aplikovány. 
* Ověřování na úrovni kanálu používá klientský certifikát, který je použit na úrovni připojení. Může také zahrnovat ověřování na úrovni volání/přihlašovací údaje autorizace pro automatické použití na každé volání kanálu. 

Ke zvýšení zabezpečení služby můžete použít jeden nebo oba tyto mechanismy.

ASP.NET Core implementace gRPC podporuje ověřování a autorizaci prostřednictvím většiny standardních ASP.NET Core mechanismů:

- Volání ověřování
  - Azure Active Directory
  - IdentityServer
  - Nosný token JWT
  - OAuth 2.0
  - OpenID Connect
  - WS-Federation
- Ověřování kanálu
  - certifikát klienta

Metody ověřování volání jsou všechny založené na *tokenech*. Jediným skutečným rozdílem je způsob, jakým se generují tokeny, a knihovny, které slouží k ověření tokenů ve službě ASP.NET Core.

Další informace najdete v článku o [ověřování a autorizaci](/aspnet/core/grpc/authn-and-authz) .

> [!NOTE]
> Pokud používáte gRPC prostřednictvím připojení HTTP/2 zašifrovaného protokolem TLS, bude veškerý provoz mezi klienty a servery zašifrovaný, i když nepoužíváte ověřování na úrovni kanálu.

V této kapitole se dozvíte, jak použít přihlašovací údaje volání a přihlašovací údaje kanálu ke službě gRPC. Zobrazí také informace o použití přihlašovacích údajů z klienta .NET Core gRPC k ověřování pomocí služby.

>[!div class="step-by-step"]
>[Předchozí](client-libraries.md)
>[Další](call-credentials.md)

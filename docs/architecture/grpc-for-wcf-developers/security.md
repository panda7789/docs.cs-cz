---
title: Zabezpečení v gRPC aplikacích – gRPC pro vývojáře WCF
description: Přehled ověřování volání a kanálu a autorizaci v gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5f3d32817ccb5d9f278d256c0ee135f0e2a17cf2
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184139"
---
# <a name="security-in-grpc-applications"></a>Zabezpečení v aplikacích gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V jakémkoli scénáři reálného světa je zabezpečení aplikací a služeb zásadní. Zabezpečení pokrývá tři klíčové oblasti: šifrování síťového provozu, aby se zabránilo jeho zachycení nesprávnými aktéry. ověřování klientů a serverů za účelem vytvoření identity a vztahu důvěryhodnosti; a autorizace klientů pro řízení přístupu k systémům a uplatnění oprávnění na základě identity.

> [!NOTE]
> **Ověřování** se týká vytvoření identity klienta nebo serveru. K určení toho, jestli má klient oprávnění pro přístup k prostředku nebo k vystavení příkazu, se jedná o **autorizaci** .

Tato kapitola se zabývá zařízeními pro ověřování a autorizaci v gRPC pro ASP.NET Core a zabývá se zabezpečením sítě pomocí šifrovaných připojení TLS.

## <a name="wcf-authentication-and-authorization"></a>Ověřování a autorizace WCF

Ověřování a autorizace ve službě WCF byly zpracovávány různými způsoby v závislosti na používaných přenosech a vazbách. Služba WCF podporuje různé standardy\* protokolu WS-Security a ověřování systému Windows pro služby HTTP spuštěné ve službě IIS nebo NetTcp Services mezi systémy Windows.

## <a name="grpc-authentication-and-authorization"></a>ověřování a autorizace gRPC

ověřování a autorizace gRPC funguje na dvou úrovních. Ověřování/autorizace na úrovni volání je obvykle zpracováváno pomocí tokenů, které jsou použity v metadatech, když je provedeno volání. Ověřování na úrovni kanálu používá klientský certifikát, který je použit na úrovni připojení, a může také zahrnovat ověřování na úrovni volání/přihlašovací údaje autorizace pro automatické použití na každé volání kanálu. K zabezpečení služby můžete použít jeden nebo oba tyto mechanismy.

ASP.NET Core implementace gRPC podporuje ověřování a autorizaci pomocí většiny standardních ASP.NET Core mechanismů:

- Volání ověřování
  - Azure Active Directory
  - IdentityServer
  - Nosný token JWT
  - OAuth 2,0
  - OpenID připojit
  - WS-Federation
- Ověřování kanálu
  - Certifikát klienta

Metody ověřování volání jsou všechny založené na *tokenech*. Jediným skutečným rozdílem je způsob, jakým se generuje token, a knihovny, které slouží k ověření tokenů ve službě ASP.NET Core.

Další informace najdete v [dokumentaci k ověřování a autorizaci na Microsoft docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).

> [!NOTE]
> Při použití gRPC prostřednictvím připojení HTTP/2 zašifrovaného protokolem TLS bude veškerý provoz mezi klienty a servery zašifrovaný i v případě, že nepoužíváte ověřování na úrovni kanálu.

V této kapitole se dozvíte, jak použít přihlašovací údaje pro volání a přihlašovací údaje kanálu ke službě gRPC a jak pomocí přihlašovacích údajů z klienta .NET Core gRPC ověřit pomocí služby.

>[!div class="step-by-step"]
>[Předchozí](client-libraries.md)
>[Další](call-credentials.md)

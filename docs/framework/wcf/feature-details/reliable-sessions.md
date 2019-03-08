---
title: Spolehlivé relace
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 9a2cd06c4c5a73d9fb5c4c7f09632e10c3eb0d87
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679123"
---
# <a name="reliable-sessions"></a>Spolehlivé relace

Tato část popisuje, co Windows Communication Foundation (WCF) stabilní relace se nachází, co se používá pro, jak a kdy Pokud chcete použít jeden, jaký konfigurace vazby na ně a ukazatelů na osvědčené postupy. Následující tabulka shrnuje informace o základní body a související témata v této části.

Spolehlivá relace WCF poskytuje funkce zajistit, aby se přenesou pomocí zprostředkovatelů SOAP nebo přenos zprávy odesílané mezi koncovými body a jsou poskytována pouze jednou a volitelně také ve stejném pořadí, ve kterém byly odeslány.

Pro použití s WCF aplikace stabilní relace, použijte jednu z vazeb poskytovaných systémem ve službě WCF, které podporují stabilní relace, ve výchozím nastavení nebo jako možnost, nebo vytvořte vlastní vlastní vazby, který podporuje relace.

## <a name="in-this-section"></a>V tomto oddílu

[Spolehlivé relace – přehled](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) popisuje spolehlivé relace, kdy je jiný vazby, které podporují spolehlivé relace, můžete použít a jak pracují.

[Postupy: Exchange zprávy v rámci stabilní relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) popisuje, jak na vytvoření stabilní relace přes protokol HTTP pomocí zadaného v konfiguraci vlastní vazby.

[Postupy: Zabezpečené zprávy ve spolehlivých relacích](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) popisuje, jak zabezpečit stabilní relace.

[Postupy: Vytvoření vazba vlastní spolehlivé relaci s HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) popisuje, jak na vytvoření stabilní relace přes protokol HTTPS.

[Osvědčené postupy pro spolehlivé relace](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) obsahuje také popis některých doporučených postupů spojených s použitím stabilní relace.

## <a name="reference"></a>Odkaz

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Viz také:

- [Fronty a spolehlivé relace](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
- [Relace, vytváření instancí a souběžnost](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)

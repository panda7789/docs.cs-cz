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
ms.openlocfilehash: 910ad952192243c6aa8a79417ad711d8c2a4ba2e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590537"
---
# <a name="reliable-sessions"></a>Spolehlivé relace

Tato část popisuje, co je spolehlivá relace Windows Communication Foundation (WCF), co se používá pro, jak a kdy se má použít, co konfigurace vazby podporuje a odkazuje na osvědčené postupy. Následující tabulka shrnuje podrobnosti o základních bodech a souvisejících tématech v této části.

Technologie WCF spolehlivé relace poskytuje funkce, které zajišťují, aby se zprávy odesílané mezi koncovými body přenesly prostřednictvím zprostředkovatele SOAP nebo přenosu, a jsou dodávány pouze jednou a případně ve stejném pořadí, v jakém byly odeslány.

Chcete-li použít spolehlivé relace s aplikací WCF, buď použijte jednu ze systémem poskytnutých vazeb ve službě WCF, která podporuje spolehlivé relace ve výchozím nastavení, nebo jako možnost nebo vytvořte vlastní vazbu, která podporuje relaci.

## <a name="in-this-section"></a>V tomto oddílu

[Přehled spolehlivých relací](reliable-sessions-overview.md) Popisuje spolehlivé relace, kdy je budete používat, různé vazby, které podporují spolehlivé relace a jak fungují.

[Postupy: Výměna zpráv v rámci spolehlivé relace](how-to-exchange-messages-within-a-reliable-session.md) Popisuje, jak vytvořit spolehlivou relaci přes protokol HTTP pomocí vlastní vazby zadané v konfiguraci.

[Postupy: zabezpečení zpráv v rámci spolehlivých relací](how-to-secure-messages-within-reliable-sessions.md) Popisuje, jak zabezpečit spolehlivou relaci.

[Postupy: Vytvoření vlastní vazby spolehlivé relace s protokolem HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Popisuje, jak vytvořit spolehlivou relaci přes protokol HTTPS.

[Osvědčené postupy pro spolehlivé relace](best-practices-for-reliable-sessions.md) Popisuje některé z osvědčených postupů spojených s používáním spolehlivé relace.

## <a name="reference"></a>Referenční informace

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Viz také

- [Fronty a spolehlivé relace](queues-and-reliable-sessions.md)
- [Relace, vytváření instancí a souběžnost](sessions-instancing-and-concurrency.md)

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
ms.openlocfilehash: 396c76cbdb8eada881a5c87edfc2500dcdab3ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497162"
---
# <a name="reliable-sessions"></a>Spolehlivé relace

Tato část popisuje jaké Windows Communication Foundation (WCF) je spolehlivé relace, čemu se používá, jak a kdy použít jednu, jaký vazby konfigurace podporují, a ukazatele na osvědčené postupy. Následující tabulka shrnuje informace o základní body a související témata v této části.

Spolehlivá relace WCF poskytuje featrues zajištění, že zprávy odeslané mezi koncovými body se přenesou pomocí protokolu SOAP nebo přenos prostředníci a se dodávají jenom jednou a volitelně ve stejném pořadí, ve které byly odeslány.

Spolehlivá relace používat s aplikací WCF, použijte jednu poskytované systémem vazbách ve WCF, které podporují spolehlivé relace ve výchozím nastavení, nebo jako možnost, nebo vytvořte vlastní vlastní vazby, která podporuje relace.

## <a name="in-this-section"></a>V tomto oddílu

[Spolehlivé relace – přehled](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)   
Popisuje spolehlivé relace, jejich různých vazby, které podporují spolehlivé relace, použití a jak pracují.

[Postupy: výměna zpráv ve spolehlivých relacích](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)   
Popisuje postup vytvoření spolehlivé relace přes protokol HTTP pomocí vlastní vazby v konfiguraci zadána.

[Postupy: zabezpečené zprávy ve spolehlivých relacích](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)   
Popisuje, jak zabezpečit spolehlivé relace.

[Postupy: vytvoření vazby vlastní spolehlivé relace s protokolem HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)   
Popisuje postup vytvoření spolehlivé relace přes protokol HTTPS.

[Osvědčené postupy pro spolehlivé relace](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)   
Popisuje některé osvědčené postupy související s používáním spolehlivé relace.

## <a name="reference"></a>Odkaz

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Viz také

[Fronty a spolehlivé relace](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)   
[Relace, vytváření instancí a souběžnost](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)

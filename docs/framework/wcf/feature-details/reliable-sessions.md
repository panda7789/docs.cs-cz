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
# <a name="reliable-sessions"></a><span data-ttu-id="5fa40-102">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="5fa40-102">Reliable Sessions</span></span>

<span data-ttu-id="5fa40-103">Tato část popisuje, co je spolehlivá relace Windows Communication Foundation (WCF), co se používá pro, jak a kdy se má použít, co konfigurace vazby podporuje a odkazuje na osvědčené postupy.</span><span class="sxs-lookup"><span data-stu-id="5fa40-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="5fa40-104">Následující tabulka shrnuje podrobnosti o základních bodech a souvisejících tématech v této části.</span><span class="sxs-lookup"><span data-stu-id="5fa40-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="5fa40-105">Technologie WCF spolehlivé relace poskytuje funkce, které zajišťují, aby se zprávy odesílané mezi koncovými body přenesly prostřednictvím zprostředkovatele SOAP nebo přenosu, a jsou dodávány pouze jednou a případně ve stejném pořadí, v jakém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="5fa40-105">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="5fa40-106">Chcete-li použít spolehlivé relace s aplikací WCF, buď použijte jednu ze systémem poskytnutých vazeb ve službě WCF, která podporuje spolehlivé relace ve výchozím nastavení, nebo jako možnost nebo vytvořte vlastní vazbu, která podporuje relaci.</span><span class="sxs-lookup"><span data-stu-id="5fa40-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5fa40-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5fa40-107">In This Section</span></span>

<span data-ttu-id="5fa40-108">[Přehled spolehlivých relací](reliable-sessions-overview.md) Popisuje spolehlivé relace, kdy je budete používat, různé vazby, které podporují spolehlivé relace a jak fungují.</span><span class="sxs-lookup"><span data-stu-id="5fa40-108">[Reliable Sessions Overview](reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="5fa40-109">[Postupy: Výměna zpráv v rámci spolehlivé relace](how-to-exchange-messages-within-a-reliable-session.md) Popisuje, jak vytvořit spolehlivou relaci přes protokol HTTP pomocí vlastní vazby zadané v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5fa40-109">[How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="5fa40-110">[Postupy: zabezpečení zpráv v rámci spolehlivých relací](how-to-secure-messages-within-reliable-sessions.md) Popisuje, jak zabezpečit spolehlivou relaci.</span><span class="sxs-lookup"><span data-stu-id="5fa40-110">[How to: Secure Messages within Reliable Sessions](how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="5fa40-111">[Postupy: Vytvoření vlastní vazby spolehlivé relace s protokolem HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Popisuje, jak vytvořit spolehlivou relaci přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5fa40-111">[How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="5fa40-112">[Osvědčené postupy pro spolehlivé relace](best-practices-for-reliable-sessions.md) Popisuje některé z osvědčených postupů spojených s používáním spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="5fa40-112">[Best Practices for Reliable Sessions](best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="5fa40-113">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="5fa40-113">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="5fa40-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fa40-114">See also</span></span>

- [<span data-ttu-id="5fa40-115">Fronty a spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="5fa40-115">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
- [<span data-ttu-id="5fa40-116">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="5fa40-116">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)

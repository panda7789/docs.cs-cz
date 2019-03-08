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
# <a name="reliable-sessions"></a><span data-ttu-id="d4648-102">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="d4648-102">Reliable Sessions</span></span>

<span data-ttu-id="d4648-103">Tato část popisuje, co Windows Communication Foundation (WCF) stabilní relace se nachází, co se používá pro, jak a kdy Pokud chcete použít jeden, jaký konfigurace vazby na ně a ukazatelů na osvědčené postupy.</span><span class="sxs-lookup"><span data-stu-id="d4648-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="d4648-104">Následující tabulka shrnuje informace o základní body a související témata v této části.</span><span class="sxs-lookup"><span data-stu-id="d4648-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="d4648-105">Spolehlivá relace WCF poskytuje funkce zajistit, aby se přenesou pomocí zprostředkovatelů SOAP nebo přenos zprávy odesílané mezi koncovými body a jsou poskytována pouze jednou a volitelně také ve stejném pořadí, ve kterém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="d4648-105">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="d4648-106">Pro použití s WCF aplikace stabilní relace, použijte jednu z vazeb poskytovaných systémem ve službě WCF, které podporují stabilní relace, ve výchozím nastavení nebo jako možnost, nebo vytvořte vlastní vlastní vazby, který podporuje relace.</span><span class="sxs-lookup"><span data-stu-id="d4648-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d4648-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d4648-107">In This Section</span></span>

<span data-ttu-id="d4648-108">[Spolehlivé relace – přehled](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) popisuje spolehlivé relace, kdy je jiný vazby, které podporují spolehlivé relace, můžete použít a jak pracují.</span><span class="sxs-lookup"><span data-stu-id="d4648-108">[Reliable Sessions Overview](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="d4648-109">[Postupy: Exchange zprávy v rámci stabilní relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) popisuje, jak na vytvoření stabilní relace přes protokol HTTP pomocí zadaného v konfiguraci vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d4648-109">[How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="d4648-110">[Postupy: Zabezpečené zprávy ve spolehlivých relacích](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) popisuje, jak zabezpečit stabilní relace.</span><span class="sxs-lookup"><span data-stu-id="d4648-110">[How to: Secure Messages within Reliable Sessions](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="d4648-111">[Postupy: Vytvoření vazba vlastní spolehlivé relaci s HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) popisuje, jak na vytvoření stabilní relace přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d4648-111">[How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="d4648-112">[Osvědčené postupy pro spolehlivé relace](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) obsahuje také popis některých doporučených postupů spojených s použitím stabilní relace.</span><span class="sxs-lookup"><span data-stu-id="d4648-112">[Best Practices for Reliable Sessions](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="d4648-113">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d4648-113">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="d4648-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4648-114">See also</span></span>

- [<span data-ttu-id="d4648-115">Fronty a spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="d4648-115">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
- [<span data-ttu-id="d4648-116">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="d4648-116">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)

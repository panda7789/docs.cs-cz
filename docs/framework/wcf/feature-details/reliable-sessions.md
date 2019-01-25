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
ms.openlocfilehash: 1d87f6f4d94763dc8f6ac7e929c22b17940097ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735421"
---
# <a name="reliable-sessions"></a><span data-ttu-id="7b543-102">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="7b543-102">Reliable Sessions</span></span>

<span data-ttu-id="7b543-103">Tato část popisuje, co Windows Communication Foundation (WCF) stabilní relace se nachází, co se používá pro, jak a kdy Pokud chcete použít jeden, jaký konfigurace vazby na ně a ukazatelů na osvědčené postupy.</span><span class="sxs-lookup"><span data-stu-id="7b543-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="7b543-104">Následující tabulka shrnuje informace o základní body a související témata v této části.</span><span class="sxs-lookup"><span data-stu-id="7b543-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="7b543-105">Spolehlivá relace WCF poskytuje featrues zajištění, že se přenesou pomocí zprostředkovatelů SOAP nebo přenos zprávy odesílané mezi koncovými body a jsou poskytována pouze jednou a volitelně také ve stejném pořadí, ve kterém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="7b543-105">The reliable session WCF provides featrues ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="7b543-106">Pro použití s WCF aplikace stabilní relace, použijte jednu z vazeb poskytovaných systémem ve službě WCF, které podporují stabilní relace, ve výchozím nastavení nebo jako možnost, nebo vytvořte vlastní vlastní vazby, který podporuje relace.</span><span class="sxs-lookup"><span data-stu-id="7b543-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7b543-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7b543-107">In This Section</span></span>

<span data-ttu-id="7b543-108">[Spolehlivé relace – přehled](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="7b543-108">[Reliable Sessions Overview](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span></span>  
<span data-ttu-id="7b543-109">Popisuje spolehlivé relace, kdy je jiný vazby, které podporují spolehlivé relace, můžete použít a jak pracují.</span><span class="sxs-lookup"><span data-stu-id="7b543-109">Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="7b543-110">[Postupy: Výměna zpráv ve spolehlivých relacích](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span><span class="sxs-lookup"><span data-stu-id="7b543-110">[How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span></span>  
<span data-ttu-id="7b543-111">Popisuje, jak na vytvoření stabilní relace přes protokol HTTP pomocí zadaného v konfiguraci vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="7b543-111">Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="7b543-112">[Postupy: Zabezpečené zprávy ve spolehlivých relacích](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="7b543-112">[How to: Secure Messages within Reliable Sessions](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span></span>  
<span data-ttu-id="7b543-113">Popisuje, jak zabezpečit stabilní relace.</span><span class="sxs-lookup"><span data-stu-id="7b543-113">Describes how to secure a reliable session.</span></span>

<span data-ttu-id="7b543-114">[Postupy: Vytvoření vazby vlastního stabilní relaci s HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span><span class="sxs-lookup"><span data-stu-id="7b543-114">[How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span></span>  
<span data-ttu-id="7b543-115">Popisuje, jak na vytvoření stabilní relace přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7b543-115">Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="7b543-116">[Osvědčené postupy pro spolehlivé relace](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="7b543-116">[Best Practices for Reliable Sessions](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span></span>  
<span data-ttu-id="7b543-117">Obsahuje také popis některých doporučených postupů spojených s použitím stabilní relace.</span><span class="sxs-lookup"><span data-stu-id="7b543-117">Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="7b543-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="7b543-118">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="7b543-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b543-119">See also</span></span>

- [<span data-ttu-id="7b543-120">Fronty a spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="7b543-120">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
- [<span data-ttu-id="7b543-121">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="7b543-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)

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
# <a name="reliable-sessions"></a><span data-ttu-id="3a612-102">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="3a612-102">Reliable Sessions</span></span>

<span data-ttu-id="3a612-103">Tato část popisuje jaké Windows Communication Foundation (WCF) je spolehlivé relace, čemu se používá, jak a kdy použít jednu, jaký vazby konfigurace podporují, a ukazatele na osvědčené postupy.</span><span class="sxs-lookup"><span data-stu-id="3a612-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="3a612-104">Následující tabulka shrnuje informace o základní body a související témata v této části.</span><span class="sxs-lookup"><span data-stu-id="3a612-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="3a612-105">Spolehlivá relace WCF poskytuje featrues zajištění, že zprávy odeslané mezi koncovými body se přenesou pomocí protokolu SOAP nebo přenos prostředníci a se dodávají jenom jednou a volitelně ve stejném pořadí, ve které byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="3a612-105">The reliable session WCF provides featrues ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="3a612-106">Spolehlivá relace používat s aplikací WCF, použijte jednu poskytované systémem vazbách ve WCF, které podporují spolehlivé relace ve výchozím nastavení, nebo jako možnost, nebo vytvořte vlastní vlastní vazby, která podporuje relace.</span><span class="sxs-lookup"><span data-stu-id="3a612-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3a612-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3a612-107">In This Section</span></span>

<span data-ttu-id="3a612-108">[Spolehlivé relace – přehled](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="3a612-108">[Reliable Sessions Overview](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span></span>  
<span data-ttu-id="3a612-109">Popisuje spolehlivé relace, jejich různých vazby, které podporují spolehlivé relace, použití a jak pracují.</span><span class="sxs-lookup"><span data-stu-id="3a612-109">Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="3a612-110">[Postupy: výměna zpráv ve spolehlivých relacích](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span><span class="sxs-lookup"><span data-stu-id="3a612-110">[How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span></span>  
<span data-ttu-id="3a612-111">Popisuje postup vytvoření spolehlivé relace přes protokol HTTP pomocí vlastní vazby v konfiguraci zadána.</span><span class="sxs-lookup"><span data-stu-id="3a612-111">Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="3a612-112">[Postupy: zabezpečené zprávy ve spolehlivých relacích](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="3a612-112">[How to: Secure Messages within Reliable Sessions](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span></span>  
<span data-ttu-id="3a612-113">Popisuje, jak zabezpečit spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="3a612-113">Describes how to secure a reliable session.</span></span>

<span data-ttu-id="3a612-114">[Postupy: vytvoření vazby vlastní spolehlivé relace s protokolem HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span><span class="sxs-lookup"><span data-stu-id="3a612-114">[How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span></span>  
<span data-ttu-id="3a612-115">Popisuje postup vytvoření spolehlivé relace přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3a612-115">Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="3a612-116">[Osvědčené postupy pro spolehlivé relace](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="3a612-116">[Best Practices for Reliable Sessions](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span></span>  
<span data-ttu-id="3a612-117">Popisuje některé osvědčené postupy související s používáním spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="3a612-117">Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="3a612-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="3a612-118">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="3a612-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a612-119">See Also</span></span>

<span data-ttu-id="3a612-120">[Fronty a spolehlivé relace](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="3a612-120">[Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md) </span></span>  
[<span data-ttu-id="3a612-121">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="3a612-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)

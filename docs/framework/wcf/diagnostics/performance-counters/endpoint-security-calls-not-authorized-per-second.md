---
title: 'Koncový bod: Počet neautorizovaných volání zabezpečení za sekundu'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4cefdd7480c7d0e9475b1883e603d9db1f287d4a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386621"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="acd39-102">Koncový bod: Počet neautorizovaných volání zabezpečení za sekundu</span><span class="sxs-lookup"><span data-stu-id="acd39-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="acd39-103">Název čítače: Zabezpečení počet neautorizovaných volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="acd39-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="acd39-104">Popis</span><span class="sxs-lookup"><span data-stu-id="acd39-104">Description</span></span>  
 <span data-ttu-id="acd39-105">Počet příchozích zpráv v sekundy, které se od platného uživatele a správně chráněný, ale uživatel nemá oprávnění k provádění konkrétních úkolů.</span><span class="sxs-lookup"><span data-stu-id="acd39-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="acd39-106">Tento čítač se zvyšuje při <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> vrátí metoda `false`.</span><span class="sxs-lookup"><span data-stu-id="acd39-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="acd39-107">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="acd39-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="acd39-108">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="acd39-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>

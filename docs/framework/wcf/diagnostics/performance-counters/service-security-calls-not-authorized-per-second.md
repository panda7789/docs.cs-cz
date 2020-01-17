---
title: 'Služba: Počet neautorizovaných volání zabezpečení za sekundu'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 964eff97a58ab7d5a68dbc1891473ae8d04a50ad
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163875"
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="d438f-102">Služba: Počet neautorizovaných volání zabezpečení za sekundu</span><span class="sxs-lookup"><span data-stu-id="d438f-102">Service: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="d438f-103">Název čítače: počet neautorizovaných volání zabezpečení za sekundu</span><span class="sxs-lookup"><span data-stu-id="d438f-103">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="d438f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="d438f-104">Description</span></span>  
 <span data-ttu-id="d438f-105">Počet příchozích zpráv za sekundu, které jsou z platného uživatele a správně chráněny, ale uživatel není autorizovaný k provádění konkrétních úkolů.</span><span class="sxs-lookup"><span data-stu-id="d438f-105">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="d438f-106">Hodnota tohoto čítače se zvýší, když metoda <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="d438f-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="d438f-107">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="d438f-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d438f-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="d438f-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>

---
title: Počet neautorizovaných volání zabezpečení za sekundu
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 2986ba241ef9b6c110a4742f77320469cdf5f07a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163927"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="2fffe-102">Počet neautorizovaných volání zabezpečení za sekundu</span><span class="sxs-lookup"><span data-stu-id="2fffe-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="2fffe-103">Název čítače: počet neautorizovaných volání zabezpečení za sekundu</span><span class="sxs-lookup"><span data-stu-id="2fffe-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2fffe-104">Popis</span><span class="sxs-lookup"><span data-stu-id="2fffe-104">Description</span></span>  
 <span data-ttu-id="2fffe-105">Počet volání, jejichž autorizace v této operaci se nezdařila, za sekundu.</span><span class="sxs-lookup"><span data-stu-id="2fffe-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="2fffe-106">Hodnota tohoto čítače se zvýší, když metoda <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="2fffe-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="2fffe-107">Indikuje, že příchozí zpráva pochází z platného uživatele a je správně chráněna, ale uživatel není autorizovaný k provádění konkrétních úkolů.</span><span class="sxs-lookup"><span data-stu-id="2fffe-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="2fffe-108">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="2fffe-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2fffe-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="2fffe-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>

---
title: Počet neautorizovaných volání zabezpečení za sekundu
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d8f04abc46a85f151108653b399c238e0275bf7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473552"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="14719-102">Počet neautorizovaných volání zabezpečení za sekundu</span><span class="sxs-lookup"><span data-stu-id="14719-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="14719-103">Název čítače: Zabezpečení počet neautorizovaných volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="14719-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="14719-104">Popis</span><span class="sxs-lookup"><span data-stu-id="14719-104">Description</span></span>  
 <span data-ttu-id="14719-105">Počet volání, která se nezdařila autorizace v této operaci za sekundu.</span><span class="sxs-lookup"><span data-stu-id="14719-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="14719-106">Hodnota tohoto čítače se zvýší, když <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="14719-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="14719-107">Znamená příchozí zprávu od platného uživatele a správně chráněný, ale uživatel není autorizovaný k provést určité úlohy.</span><span class="sxs-lookup"><span data-stu-id="14719-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="14719-108">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="14719-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="14719-109">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="14719-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>

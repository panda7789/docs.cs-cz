---
title: Čítače provozního výkonu
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 59c75dacb2a01f1b85d67d5cc1651dbc55b6aa8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320167"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="7b996-102">Čítače provozního výkonu</span><span class="sxs-lookup"><span data-stu-id="7b996-102">Operation Performance Counters</span></span>
<span data-ttu-id="7b996-103">Čítače výkonu operace se při zobrazení pomocí nástroje sledování výkonu (Perfmon. exe) nacházejí v objektu výkonu `ServiceModelOperation 4.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="7b996-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="7b996-104">Každá operace má jednotlivou instanci.</span><span class="sxs-lookup"><span data-stu-id="7b996-104">Each operation has an individual instance.</span></span> <span data-ttu-id="7b996-105">To znamená, že pokud má daný kontrakt 10 operací, je k této smlouvě přidruženo 10 instancí čítače operací.</span><span class="sxs-lookup"><span data-stu-id="7b996-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="7b996-106">Instance objektů jsou pojmenovány pomocí následujícího vzoru:</span><span class="sxs-lookup"><span data-stu-id="7b996-106">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="7b996-107">Tento čítač vám umožní změřit způsob, jakým se volání používá, a to, jak dobře probíhá operace.</span><span class="sxs-lookup"><span data-stu-id="7b996-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="7b996-108">Délka názvu instance čítače výkonu je omezena.</span><span class="sxs-lookup"><span data-stu-id="7b996-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="7b996-109">Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="7b996-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b996-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b996-110">See also</span></span>

- [<span data-ttu-id="7b996-111">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="7b996-111">Performance Counters</span></span>](index.md)

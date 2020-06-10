---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: ab1c2c8afe3a66536810a614cc6deac12519cb9b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599630"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="8b030-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="8b030-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="8b030-103">Služba protokolu WS-AT obdržela zprávu o přípravě nebo přehrání z nerozpoznaného účastníka.</span><span class="sxs-lookup"><span data-stu-id="8b030-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="8b030-104">Účastník vrátil chybu, deklaruje, že výsledek transakce je nejistý.</span><span class="sxs-lookup"><span data-stu-id="8b030-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8b030-105">Popis</span><span class="sxs-lookup"><span data-stu-id="8b030-105">Description</span></span>  
 <span data-ttu-id="8b030-106">Sledováno, když místní správce transakce obdrží přípravnou nebo přepracovanou zprávu z nestálého zařazení, který již byl zapomenut.</span><span class="sxs-lookup"><span data-stu-id="8b030-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8b030-107">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="8b030-107">Troubleshooting</span></span>  
 <span data-ttu-id="8b030-108">Prozkoumejte možné příčiny zpožděných zpráv přicházejících od účastníka.</span><span class="sxs-lookup"><span data-stu-id="8b030-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b030-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b030-109">See also</span></span>

- [<span data-ttu-id="8b030-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="8b030-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="8b030-111">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="8b030-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8b030-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="8b030-112">Administration and Diagnostics</span></span>](../index.md)

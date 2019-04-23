---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: 9434f2f902a50a37fb3efee22fd3b18b33af9129
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138967"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="2d900-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="2d900-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="2d900-103">Služba protokolu WS-AT obdržela zprávu připravit nebo odpovědět od rozpoznaného nestálého účastníka.</span><span class="sxs-lookup"><span data-stu-id="2d900-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="2d900-104">Chyba byla vrácena účastníkovi, deklaruje, že výsledek transakce je zpochybněn.</span><span class="sxs-lookup"><span data-stu-id="2d900-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2d900-105">Popis</span><span class="sxs-lookup"><span data-stu-id="2d900-105">Description</span></span>  
 <span data-ttu-id="2d900-106">Trasovaná při místní správce transakcí přijme zprávu připravit nebo odpovědět od těkavých zařazení, které už se zapomene.</span><span class="sxs-lookup"><span data-stu-id="2d900-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="2d900-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="2d900-107">Troubleshooting</span></span>  
 <span data-ttu-id="2d900-108">Prošetření možných příčin opožděné zprávy přicházející z nestálého účastníka.</span><span class="sxs-lookup"><span data-stu-id="2d900-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d900-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d900-109">See also</span></span>

- [<span data-ttu-id="2d900-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="2d900-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="2d900-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="2d900-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2d900-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="2d900-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)

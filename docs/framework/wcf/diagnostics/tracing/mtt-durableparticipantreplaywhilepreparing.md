---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 31fb8d466c76c7490aa80dfcab089332af4036a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589129"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="b542a-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="b542a-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="b542a-103">Služba protokolu WS-AT obdržela zprávu o přehrání od trvalého účastníka, který nereagoval na přípravu.</span><span class="sxs-lookup"><span data-stu-id="b542a-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="b542a-104">V důsledku toho byla transakce přerušena.</span><span class="sxs-lookup"><span data-stu-id="b542a-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b542a-105">Popis</span><span class="sxs-lookup"><span data-stu-id="b542a-105">Description</span></span>  
 <span data-ttu-id="b542a-106">Sledováno, pokud je přijata zpráva o opětovném přehrání, zatímco se stále připravuje trvalý účastník.</span><span class="sxs-lookup"><span data-stu-id="b542a-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="b542a-107">Toto je neplatná zpráva pro tento stav a transakce bude přerušena.</span><span class="sxs-lookup"><span data-stu-id="b542a-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b542a-108">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="b542a-108">Troubleshooting</span></span>

<span data-ttu-id="b542a-109">Přijetí této chyby může znamenat, že trvalý účastník (včetně podřízeného TransactionManagers) se obnovil z chyby. Nejedná se však o výsledek transakce a požádá o jeho stav.</span><span class="sxs-lookup"><span data-stu-id="b542a-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b542a-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b542a-110">See also</span></span>

- [<span data-ttu-id="b542a-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="b542a-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="b542a-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="b542a-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b542a-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="b542a-113">Administration and Diagnostics</span></span>](../index.md)

---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: 2bc71d18480fa19be66cbfa1687a7b63eb548309
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601449"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="0ddb3-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="0ddb3-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="0ddb3-103">Zadaná transakce pro zadanou operaci byla dokončena z důvodu neošetřené výjimky spuštění.</span><span class="sxs-lookup"><span data-stu-id="0ddb3-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0ddb3-104">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddb3-104">Description</span></span>  
 <span data-ttu-id="0ddb3-105">Trasovat se, když dojde k chybě během pokusu o dokončení aktuální transakce.</span><span class="sxs-lookup"><span data-stu-id="0ddb3-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="0ddb3-106">K tomu dojde před odesláním odpovědi nebo chyby volajícímu.</span><span class="sxs-lookup"><span data-stu-id="0ddb3-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0ddb3-107">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="0ddb3-107">Troubleshooting</span></span>  
 <span data-ttu-id="0ddb3-108">Zkontrolujte sledovanou zprávu pro zprávu výjimky a všechny akce, které jsou k.</span><span class="sxs-lookup"><span data-stu-id="0ddb3-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ddb3-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ddb3-109">See also</span></span>

- [<span data-ttu-id="0ddb3-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="0ddb3-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="0ddb3-111">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="0ddb3-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0ddb3-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="0ddb3-112">Administration and Diagnostics</span></span>](../index.md)

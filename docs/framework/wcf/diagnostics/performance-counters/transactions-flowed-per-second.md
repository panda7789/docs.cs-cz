---
title: Počet plynoucích transakcí za sekundu
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: 8b6077af3f98f7a205772b4883dc122374083e00
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163823"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="22166-102">Počet plynoucích transakcí za sekundu</span><span class="sxs-lookup"><span data-stu-id="22166-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="22166-103">Název čítače: počet toků transakcí za sekundu</span><span class="sxs-lookup"><span data-stu-id="22166-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="22166-104">Popis</span><span class="sxs-lookup"><span data-stu-id="22166-104">Description</span></span>  
 <span data-ttu-id="22166-105">Počet transakcí, které byly do této operace předávány za sekundu.</span><span class="sxs-lookup"><span data-stu-id="22166-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="22166-106">Tento čítač se zvyšuje pokaždé, když se ve zprávě, která se pošle do operace, nachází ID transakce.</span><span class="sxs-lookup"><span data-stu-id="22166-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="22166-107">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="22166-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="22166-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="22166-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>

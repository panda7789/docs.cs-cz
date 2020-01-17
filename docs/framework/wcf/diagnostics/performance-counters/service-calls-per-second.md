---
title: 'Služba: Počet volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: be5d77169a71d6f44205a1150da5239eceff7d9c
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163901"
---
# <a name="service-calls-per-second"></a>Služba: Počet volání za sekundu
Název čítače: počet volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání této služby za sekundu.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1-N 0)/((D 1-D 0)/F) kde čitatel (N) představuje počet operací provedených během posledního ukázkového intervalu, jmenovatel (D) představuje počet taktů uplynulých během posledního ukázkového intervalu a F je frekvence impulsů.

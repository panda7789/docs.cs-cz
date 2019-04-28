---
title: Počet potvrzených zpracovaných operací za sekundu
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 124eae3b36a731ac50a147782b19c87e3adfa7be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766373"
---
# <a name="transacted-operations-committed-per-second"></a>Počet potvrzených zpracovaných operací za sekundu
Název čítače: Počet potvrzených zpracovaných operací za sekundu.  
  
## <a name="description"></a>Popis  
 Počet transakční operace, které byly v této službě potvrzen za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)

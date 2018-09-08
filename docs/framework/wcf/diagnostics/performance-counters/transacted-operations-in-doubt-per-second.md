---
title: Počet nejistých zpracovaných operací za sekundu
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: f7365c4e5f03711129916c8c6964f7e25e9b553e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194952"
---
# <a name="transacted-operations-in-doubt-per-second"></a>Počet nejistých zpracovaných operací za sekundu
Název čítače: Počet nejistých zpracovaných operací za sekundu.  
  
## <a name="description"></a>Popis  
 Počet transakční operace s nejistým nejisté v této službě za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)

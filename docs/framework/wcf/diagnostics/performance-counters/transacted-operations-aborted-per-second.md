---
title: Počet zrušených zpracovaných operací za sekundu
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: 6369fea6def5ebb6b62274caed31d5fb63b3b0e1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417479"
---
# <a name="transacted-operations-aborted-per-second"></a>Počet zrušených zpracovaných operací za sekundu
Název čítače: Stažení operací za sekundu.  
  
## <a name="description"></a>Popis  
 Počet transakční operace, které byla pravděpodobně přerušena v této službě za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)

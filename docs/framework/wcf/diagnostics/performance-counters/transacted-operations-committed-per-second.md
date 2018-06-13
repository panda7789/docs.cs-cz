---
title: Počet potvrzených zpracovaných operací za sekundu
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 3bec51a7be63c54a240b85032ecac09b87173393
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474269"
---
# <a name="transacted-operations-committed-per-second"></a>Počet potvrzených zpracovaných operací za sekundu
Název čítače: Potvrzených zpracovaných operací za sekundu.  
  
## <a name="description"></a>Popis  
 Počet transakcí operací, které byl potvrzen v rámci této služby za sekundu.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)

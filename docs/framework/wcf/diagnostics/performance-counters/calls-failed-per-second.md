---
title: Počet nezdařených volání za sekundu
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: e7c0b53f4c2b1a7e87a5791b44e452ec9146c459
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321126"
---
# <a name="calls-failed-per-second"></a>Počet nezdařených volání za sekundu
Název čítače: počet nezdařených volání za sekundu  
  
## <a name="description"></a>Popis  
 Počet volání s neošetřenými výjimkami v této operaci za sekundu  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 Tento čítač se zvýší pokaždé, když v této operaci dojde k neošetřené výjimce.  
  
## <a name="see-also"></a>Viz také:

- [Určování a zpracování chyb v kontraktech a službách](../../specifying-and-handling-faults-in-contracts-and-services.md)

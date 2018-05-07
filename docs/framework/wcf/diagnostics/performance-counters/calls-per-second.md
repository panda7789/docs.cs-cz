---
title: Počet volání za sekundu
ms.date: 03/30/2017
ms.assetid: 0efb5a94-d83b-4793-b529-6fcbedb65c43
ms.openlocfilehash: 04eb5deaf8e6eb09be4e0bf404bec11b8ce84427
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="calls-per-second"></a>Počet volání za sekundu
Název čítače: Počet volání za sekundu  
  
## <a name="description"></a>Popis  
 Počet volání s touto operací za sekundu.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)

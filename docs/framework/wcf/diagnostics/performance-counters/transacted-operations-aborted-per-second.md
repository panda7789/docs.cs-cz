---
title: "Počet zrušených zpracovaných operací za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d80d18ed1e3911b0603f930e45bda3dffaff1f75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="transacted-operations-aborted-per-second"></a>Počet zrušených zpracovaných operací za sekundu
Název čítače: Transakční operace přerušených za sekundu.  
  
## <a name="description"></a>Popis  
 Počet transakcí operací, které bylo přerušeno v rámci této služby za sekundu.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)

---
title: "Služba: Počet nezdařených volání za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2072a686d5d424f90ac2f32cf5fc11564b07542c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-failed-per-second"></a>Služba: Počet nezdařených volání za sekundu
Název čítače: Počet nezdařených volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání, které mají neošetřené výjimky a tato služba přijímá za sekundu.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)  
  
 Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybové stavy.  
  
 Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybové stavy.  
  
 Hodnota tohoto čítače se zvýší pokaždé, když dojde k neošetřené výjimce v rámci této služby.  
  
## <a name="see-also"></a>Viz také  
 [Určování a zpracování chyb v kontraktech a službách](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)

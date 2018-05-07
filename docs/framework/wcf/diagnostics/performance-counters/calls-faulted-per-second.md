---
title: Počet volání s chybou za sekundu
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: af84a379a36324131861aaa7e8577b5a44273917
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="calls-faulted-per-second"></a>Počet volání s chybou za sekundu
Název čítače: Počet volání s chybou za sekundu  
  
## <a name="description"></a>Popis  
 Počet volání, která vrátila chyby s touto operací za sekundu.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)  
  
 V aplikacích Windows Communication Foundation (WCF) metody služeb komunikaci pomocí protokolu SOAP zprávy selhání informace o chybě zpracování. Chyb SOAP jsou typy zpráv, které jsou součástí metadat pro operace služby a proto vytvoření kontraktu selhání, který můžou klienti používat, aby jejich spuštění více robustní nebo interaktivní. Vzhledem k tomu, že chyb SOAP jsou vyjádřeny klientům ve formátu XML, jsou vysoce umožňuje vzájemnou spolupráci.  
  
## <a name="see-also"></a>Viz také  
 [Určování a zpracování chyb v kontraktech a službách](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)

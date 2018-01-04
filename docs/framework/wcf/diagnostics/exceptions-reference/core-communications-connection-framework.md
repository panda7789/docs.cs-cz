---
title: "Základní komunikace: Architektura připojení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 713788f8938e43f3516edd95646fc6dc653a56c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="core-communications-connection-framework"></a>Základní komunikace: Architektura připojení
Toto téma uvádí všechny výjimky generované [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] architektura připojení.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|CloseTimedOut|Zavřít metoda vypršel časový limit po zadanou dobu. Zvyšte hodnotu časového limitu, která je předána volání zavřít nebo zvyšte hodnotu časového limitu pro uzavírání na vazby. Čas přidělený tato operace mohla být část delší časový limit.|  
|ContentTypeMismatch|Zadaný typ obsahu byla odeslána na službu, která byla očekávána zadaný. Může být neshoda vazby klienta a služby.|  
|DuplexChannelAbortedDuringOpen|Duplexní kanál do zadané ukončen během procesu otevřete.|  
|FramingValueNotAvailable|Hodnotu nelze přistupovat, protože není plně dekódovat.|  
|OperationAbortedDuringConnectionEstablishment|Operace se ukončila při navazování připojení k zadané.|  
|ReceiveTimedOut2|Po zadanou dobu vypršel časový limit operace příjmu. Čas přidělený tato operace mohla být část delší časový limit.|  
|SendCannotBeCalledAfterCloseOutputSession|Po zavolání CloseOutputSession nelze odesílat zprávy na kanál.|

---
title: 'Základní komunikace: Architektura připojení'
ms.date: 03/30/2017
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
ms.openlocfilehash: a3f52ac82c2bf09ded504e412d7f216dd0b39959
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="core-communications-connection-framework"></a>Základní komunikace: Architektura připojení
Toto téma uvádí všechny výjimky generované architektura připojení Windows Communication Foundation (WCF).  
  
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

---
title: 'Základní komunikace: Architektura připojení'
ms.date: 03/30/2017
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
ms.openlocfilehash: a3f52ac82c2bf09ded504e412d7f216dd0b39959
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998683"
---
# <a name="core-communications-connection-framework"></a>Základní komunikace: Architektura připojení
Toto téma uvádí všechny výjimky generované architektura připojení Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Řetězec prostředku|  
|-------------------|---------------------|  
|CloseTimedOut|Metoda Close skončila platnost po zadanou dobu. Zvyšte časový limit, který se předává do volání k ukončení nebo zvyšte hodnotu CloseTimeout na vazbě. Čas přidělený této operaci pravděpodobně částí delšího časového limitu.|  
|ContentTypeMismatch|Zadaný typ obsahu byl odeslán službě, která se očekávala zadaný. Vazby klienta a služby se pravděpodobně neshodují.|  
|DuplexChannelAbortedDuringOpen|Duplexní kanál do zadaného byl ukončen během otevřeného procesu.|  
|FramingValueNotAvailable|Hodnotu nejde získat přístup, protože není plně dekódována.|  
|OperationAbortedDuringConnectionEstablishment|Operace byla ukončena při navazování připojení k zadané.|  
|ReceiveTimedOut2|Operace obdržení vypršel po určeném čase. Čas přidělený této operaci pravděpodobně částí delšího časového limitu.|  
|SendCannotBeCalledAfterCloseOutputSession|Po zavolání CloseOutputSession nelze odesílat zprávy v kanálu.|

---
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 5e157da25829a0741de988d1d6dde0318a93b109
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663723"
---
# <a name="msmq"></a>MSMQ
V aplikaci služby MSMQ se přenesou žádná další aktivita v kanálu ve frontě MSMQ a ze služby MSMQ pro kanálu ve frontě.  
  
 Kromě toho ID zprávy služby MSMQ a ID zprávy protokolu SOAP (spolu s ID aktivity, pokud existuje) jsou trasovány jako součást kanálu ve frontě trasování na operace odeslání.  
  
 ID zprávy služby MSMQ a ID zprávy protokolu SOAP (spolu s aktivity, které ID, pokud existuje) jsou trasovány jako součást kanálu ve frontě trasování na operace obdržení.  
  
 Požadované přenosy na operace obdržení provádějí podobně jako ostatní přenosu (přijímání bajtů -> zpracovat zprávu -> operace).

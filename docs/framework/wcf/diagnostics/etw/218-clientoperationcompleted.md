---
title: "218 – ClientOperationCompleted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d5b6fcc1c7ec4dd2f2c008e9d8bcfb58b2b4991
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="218---clientoperationcompleted"></a>218 – ClientOperationCompleted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|218|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované klienti hned po dokončení operace. U Jednosměrná operace nastavení je to hned po odeslání zprávy jsou úspěšně. Pro operace požadavků a odpovědí jde po obdržení odpovědi.  
  
## <a name="message"></a>Zpráva  
 Klient dokončit provádění akce '%1' přidružené ke smlouvě '%2'. Zpráva byla odeslána na '%3'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Akce|xs:String|Hlavička protokolu SOAP akce odchozí zprávy.|  
|Název smlouvy|`xs:string`|Název smlouvy. Příklad: ICalculator.|  
|Cílový|`xs:string`|Adresa koncového bodu služby, který vám byl zaslán zprávy.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}. Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|

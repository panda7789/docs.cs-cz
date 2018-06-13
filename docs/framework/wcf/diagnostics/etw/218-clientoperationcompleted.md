---
title: 218 – ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 83f39be84a8d62962b85652b0e39b537c92e612c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457971"
---
# <a name="218---clientoperationcompleted"></a>218 – ClientOperationCompleted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|218|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
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
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|

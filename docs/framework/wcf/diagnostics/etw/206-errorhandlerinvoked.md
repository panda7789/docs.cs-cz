---
title: 206 – ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781924"
---
# <a name="206---errorhandlerinvoked"></a>206 – ErrorHandlerInvoked
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|206|  
|klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován po `ErrorHandler` zaznamenala příležitosti ke zpracování výjimky, ke které došlo v operaci služby.  
  
## <a name="message"></a>Zpráva  
 Dispečer vyvolal rutinu ErrorHandler typu '%1' se výjimka typu '%3'. ErrorHandled == '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Celý název CLR typu vyvolanou `ErrorHandler`.|  
|Zpracování|`xs:unsignedByte`|`true` Pokud obslužná rutina chyb zpracovává chyby, v opačném případě `false`.|  
|ExceptionTypeName|`xs:string`|Celý název CLR výjimky, která se právě zpracovává.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|

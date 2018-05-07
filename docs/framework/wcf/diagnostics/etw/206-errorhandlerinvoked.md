---
title: 206 – ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="206---errorhandlerinvoked"></a>206 – ErrorHandlerInvoked
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|206|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované po `ErrorHandler` zaznamenala příležitost ke zpracování výjimky, k níž došlo v operaci služby.  
  
## <a name="message"></a>Zpráva  
 Dispečer vyvolat ZpracováníChyby typu "%1, s výjimkou typu"%3". ErrorHandled == '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Položka FullName CLR typu vyvolanou `ErrorHandler`.|  
|Zpracovává|`xs:unsignedByte`|`true` Pokud obslužná rutina chyb zpracovávat chyby, jinak `false`.|  
|ExceptionTypeName|`xs:string`|Položka FullName CLR výjimky, která se právě zpracovává.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|

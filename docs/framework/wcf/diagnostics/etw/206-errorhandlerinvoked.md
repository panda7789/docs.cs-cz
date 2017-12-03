---
title: "206 – ErrorHandlerInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ff48217b1430002e1590ec3fdb1707d65075ffe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="206---errorhandlerinvoked"></a>206 – ErrorHandlerInvoked
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|206|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované po `ErrorHandler` zaznamenala příležitost ke zpracování výjimky, k níž došlo v operaci služby.  
  
## <a name="message"></a>Zpráva  
 Dispečer vyvolat ZpracováníChyby typu "%1, s výjimkou typu"%3". ErrorHandled == '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Položka FullName CLR typu vyvolanou `ErrorHandler`.|  
|Zpracovává|`xs:unsignedByte`|`true`Pokud obslužná rutina chyb zpracovávat chyby, jinak `false`.|  
|ExceptionTypeName|`xs:string`|Položka FullName CLR výjimky, která se právě zpracovává.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}. Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|

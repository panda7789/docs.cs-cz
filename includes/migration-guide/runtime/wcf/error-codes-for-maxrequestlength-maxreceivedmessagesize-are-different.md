---
ms.openlocfilehash: c9d6111edcfeec6852f23cc0768833de32e61022
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235279"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>Kódy chyb pro maxRequestLength nebo maxReceivedMessageSize se liší

|   |   |
|---|---|
|Podrobnosti|Zprávy ve službě WCF web služby hostované v Internetové informační služby (IIS) nebo vývojový Server ASP.NET, které překračují maxRequestLength (v technologii ASP.NET) nebo maxReceivedMessageSize (v WCF) mají různé chybové codeThe HTTP stavový kód byl změněn z 400 (Chybný požadavek ) na 413 (příliš velký požadavek Entity) a zprávy, které překračují buď nastavení maxReceivedMessageSize nebo maxRequestLength vyvolat <xref:System.ServiceModel.ProtocolException?displayProperty=name> výjimky. To zahrnuje případy, ve kterých je režim přenosu nedochází.|
|Doporučení|Tato změna usnadňuje ladění v případech, kde délka zprávy překročí limity povolené rozhraním ASP.NET nebo WCF. Je třeba upravit jakýkoli kód, který provádí zpracování založené na stavovém kódu HTTP 400.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|

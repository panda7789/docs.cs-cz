---
title: Transport integrace MSMQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bf9893a-fbd1-41fc-b6de-a41a44279936
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 18dd1262c572a7e8844d9fe2beb5de7f52c28e1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="msmq-integration-transport"></a>Transport integrace MSMQ
Toto téma uvádí všechny výjimky generované Transport integrace MSMQ.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|MessageSizeMustBeInIntegerRange|Tento objekt pro vytváření vyrovnávacích pamětí zpráv, takže velikost zprávy musí být v rozsahu celočíselnou hodnotu.|  
|MsmqByteArrayBodyExpected|Došlo k neshodě mezi zadaný formát serializace a tělo zprávy služby MSMQ. Nelze odesílat nebo přijímat zprávy. Formát serializace ByteArray vyžaduje tělo zprávy služby MSMQ být typu byte [].|  
|MsmqCannotDeserializeActiveXMessage|Došlo k chybě serializace ActiveX. Nelze odesílat nebo přijímat zprávy. Zadaný typ varianty pro tělo neodpovídá skutečné tělo zprávy služby MSMQ.|  
|MsmqCannotUseBodyTypeWithActiveXSerialization|Vlastnosti zprávy se neshodují. Nelze odesílat nebo přijímat zprávy. Vlastnost BodyType zpráva nemůže být zadán, pokud se používá formát serializace ActiveX.|  
|MsmqInvalidServiceOperationForMsmqIntegrationBinding|MsmqIntegrationBinding ověření se nezdařilo. Koncový bod služby nelze spustit. Zadaná vazba nepodporuje podpis metody pro operaci zadané služby v zadané kontraktu. Použít MsmqIntegrationBinding operace služby, opravte ji.|  
|MsmqInvalidTypeDeserialization|Serializace ActiveX se nezdařila, protože nemůže rozpoznat formát serializace. Nelze odesílat nebo přijímat zprávy.|  
|MsmqInvalidTypeSerialization|Typ variant nebyl rozpoznán. Serializace ActiveX se nezdařila. Nelze odesílat nebo přijímat zprávy. Zadaný typ variant není podporován.|  
|MsmqStreamBodyExpected|Došlo k neshodě mezi formát serializace a text obsahu. Nelze odesílat nebo přijímat zprávy. Pouze jeden typ datového proudu lze odeslat nebo pomocí režimu serializace datového proudu.|

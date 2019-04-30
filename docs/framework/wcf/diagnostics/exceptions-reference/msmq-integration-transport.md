---
title: Transport integrace MSMQ
ms.date: 03/30/2017
ms.assetid: 2bf9893a-fbd1-41fc-b6de-a41a44279936
ms.openlocfilehash: 52fd98354ded57bd7d7c075d4f08ca543760e598
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777361"
---
# <a name="msmq-integration-transport"></a>Transport integrace MSMQ
Toto téma uvádí všechny výjimky generované Transport integrace MSMQ.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Řetězec prostředku|  
|-------------------|---------------------|  
|MessageSizeMustBeInIntegerRange|Tento objekt pro vytváření vyrovnávacích pamětí zpráv, takže velikost zpráv musí být v rozsahu hodnoty celých čísel.|  
|MsmqByteArrayBodyExpected|Došlo k neshodě mezi zadaný formát serializace a tělo zprávy služby MSMQ. Zprávu nelze odeslat ani přijmout. Formát serializace třídy ByteArray vyžaduje, aby text zprávy služby MSMQ byl typu byte [].|  
|MsmqCannotDeserializeActiveXMessage|Došlo k chybě serializace ActiveX. Zprávu nelze odeslat ani přijmout. Zadaný typ variant pro text neodpovídá skutečnému textu zprávy MSMQ.|  
|MsmqCannotUseBodyTypeWithActiveXSerialization|Vlastnosti zprávy se neshodují. Zprávu nelze odeslat ani přijmout. Vlastnost BodyType zprávy nelze zadat, pokud je používán formát serializace ActiveX.|  
|MsmqInvalidServiceOperationForMsmqIntegrationBinding|Ověřování třídy MsmqIntegrationBinding se nezdařilo. Koncový bod služby nelze spustit. Zadaná vazba nepodporuje podpis metody pro operace určené služby v zadané kontraktu. Opravte operaci služby použít třídu MsmqIntegrationBinding.|  
|MsmqInvalidTypeDeserialization|Serializace ActiveX se nezdařila, protože formát serializace nelze rozpoznat. Zprávu nelze odeslat ani přijmout.|  
|MsmqInvalidTypeSerialization|Typ variant nebyl rozpoznán. Serializace ActiveX se nezdařila. Zprávu nelze odeslat ani přijmout. Zadaný typ variant není podporován.|  
|MsmqStreamBodyExpected|Neshoda mezi formátem serializace a text obsahu. Zprávu nelze odeslat ani přijmout. Pouze text typ datového proudu můžete odeslány nebo přijaty pomocí serializace režimu datového proudu.|

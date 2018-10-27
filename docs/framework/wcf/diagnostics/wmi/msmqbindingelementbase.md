---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: e7f4cf41168bd1e5483524195e20541d896a6569
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183188"
---
# <a name="msmqbindingelementbase"></a>MsmqBindingElementBase
MsmqBindingElementBase  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída MsmqBindingElementBase nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída MsmqBindingElementBase má následující vlastnosti:  
  
### <a name="customdeadletterqueue"></a>customDeadLetterQueue  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Identifikátor URI, který obsahuje umístění fronty nedoručených zpráv pro každou aplikaci, kde jsou umístěny zprávy, jejichž platnost vypršela nebo které selhaly, přenos nebo doručení.  
  
### <a name="deadletterqueue"></a>deadLetterQueue  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota výčtu, která určuje typ fronty nepoužívaných dopisů používat.  
  
### <a name="durable"></a>trvalý  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje, zda zprávy zpracované touto vazbou jsou trvalé nebo přechodné.  
  
### <a name="exactlyonce"></a>exactlyOnce  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, zda zprávy zpracované touto vazbou budou obdrženy pouze jednou.  
  
### <a name="maxretrycycles"></a>maxRetryCycles  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet opakovaných cyklů pokusů o doručení zpráv do přijímající aplikace.  
  
### <a name="receiveerrorhandling"></a>receiveErrorHandling  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastavení pro manipulaci s nezpracovatelnými zprávami.  
  
### <a name="receiveretrycount"></a>receiveRetryCount  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet okamžitých opakovaných pokusů o zprávu, která je načtena z fronty aplikace.  
  
### <a name="retrycycledelay"></a>retryCycleDelay  
 Datový typ: datum a čas  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje časovou prodlevu mezi opakovanými cykly při pokusu o doručení zprávy, která nemohla být doručena okamžitě.  
  
### <a name="timetolive"></a>timeToLive  
 Datový typ: datum a čas  
  
 Přístup k typu: jen pro čtení  
  
 Interval času, který označuje dobu zprávy zpracované touto vazbou může být ve frontě před vypršením jejich platnosti.  
  
### <a name="usemsmqtracing"></a>useMsmqTracing  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, zda zprávy zpracované touto vazbou mají být vyvolány.  
  
### <a name="usesourcejournal"></a>useSourceJournal  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, zda kopie zpráv zpracovaných touto vazbou uskladněny ve frontě deníku zdroje.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>

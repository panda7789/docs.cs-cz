---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 9a9d48cc49b19f737236939c83a4e9421013f48f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486598"
---
# <a name="msmqbindingelementbase"></a>MsmqBindingElementBase
MsmqBindingElementBase  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
 Identifikátor URI, který obsahuje umístění fronty nedoručených zpráv pro každou aplikaci, kde jsou umístěny zprávy, jejichž platnost vypršela nebo které selhaly přenos nebo doručení.  
  
### <a name="deadletterqueue"></a>deadLetterQueue  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota výčtu, která určuje typ fronty nedoručených zpráv používat.  
  
### <a name="durable"></a>trvanlivý  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje, zda jsou zprávy zpracovávané touto vazbou trvalé nebo přechodné.  
  
### <a name="exactlyonce"></a>exactlyOnce  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, zda jsou zprávy zpracovávané touto vazbou obdrženy pouze jednou.  
  
### <a name="maxretrycycles"></a>maxRetryCycles  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet cyklů opakování pokusu o doručení zprávy do přijímající aplikace.  
  
### <a name="receiveerrorhandling"></a>receiveErrorHandling  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastavení pro zpracování poškozených zpráv.  
  
### <a name="receiveretrycount"></a>receiveRetryCount  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet okamžitou opakování pokusů na zprávu, která je pro čtení z fronty aplikace.  
  
### <a name="retrycycledelay"></a>retryCycleDelay  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Hodnotu, která určuje prodlevu mezi opakování cyklů při pokusu o doručení zprávy, která nelze doručit okamžitě.  
  
### <a name="timetolive"></a>TimeToLive  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Interval času, která určuje, jak dlouho zprávy zpracovávané touto vazbou může být ve frontě před vypršením jejich platnosti.  
  
### <a name="usemsmqtracing"></a>useMsmqTracing  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která označuje, zda zprávy zpracovávané touto vazbou má trasovat.  
  
### <a name="usesourcejournal"></a>useSourceJournal  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, zda by měly být uložené kopie zprávy zpracovávané touto vazbou ve frontě deníku zdroje.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>

---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 2f04e6794342d7bd0acd51481efcbeceb04fd459
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486639"
---
# <a name="reliablesessionbindingelement"></a>ReliableSessionBindingElement
ReliableSessionBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída třídu ReliableSessionBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída třídu ReliableSessionBindingElement má následující vlastnosti:  
  
### <a name="acknowledgementinterval"></a>AcknowledgementInterval  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Časový interval, který cíl vyčkat před odesláním potvrzení zdroj zprávy na spolehlivé kanály, které jsou vytvořené pomocí objektu pro vytváření.  
  
### <a name="flowcontrolenabled"></a>FlowControlEnabled  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, zda je povoleno řízení toku.  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Určuje maximální dobu, po které bude kanál povolit druhou stranou komunikuje posílat žádné zprávy před přerušením kanálu.  
  
### <a name="maxpendingchannels"></a>MaxPendingChannels  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet kanálů, které může čekat třeba přijmout na naslouchací proces.  
  
### <a name="maxretrycount"></a>MaxRetryCount  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet pokusů, kolikrát spolehlivé kanál pokusí znovu pošlou zprávu neobdržel potvrzení, voláním `Send` na jeho základní kanálu.  
  
### <a name="maxtransferwindowsize"></a>MaxTransferWindowSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální přenosovou velikost okna pro spolehlivé relace.  
  
### <a name="ordered"></a>řazení  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, zda jsou zprávy zaručené doručení v pořadí, ve kterém byly odeslány.  
  
### <a name="reliablemessagingversion"></a>ReliableMessagingVersion  
 Datový typ: celé číslo  
  
 Přístup k typu: jen pro čtení  
  
 Celé číslo, které určuje verzi protokolu WS-ReliableMessaging použít v spolehlivé relace.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>

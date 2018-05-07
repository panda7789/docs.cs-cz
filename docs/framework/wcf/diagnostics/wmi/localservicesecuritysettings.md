---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8f80af782c474ccf3a232ab353125fa223d4f5d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings
LocalServiceSecuritySettings  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída LocalServiceSecuritySettings nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída LocalServiceSecuritySettings má následující vlastnosti:  
  
### <a name="detectreplays"></a>DetectReplays  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, jestli jsou před zneužitím útoky na kanál zjistil a řešeny automaticky.  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet čekající na vyřízení zabezpečení relací, které služba podporuje.  
  
### <a name="issuedcookielifetime"></a>IssuedCookieLifetime  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Časový interval, který určuje životnost vystaveno pro všechny nové soubory cookie zabezpečení.  
  
### <a name="maxcachedcookies"></a>MaxCachedCookies  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet souborů cookie, které mohou být uloženy v mezipaměti.  
  
### <a name="maxclockskew"></a>Maxclockskew –  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Časový interval, který určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran.  
  
### <a name="maxpendingsessions"></a>MaxPendingSessions  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet čekajících připojení služby.  
  
### <a name="maxstatefulnegotiations"></a>MaxStatefulNegotiations  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Počet vyjednávání zabezpečení, které mohou být souběžně aktivní.  
  
### <a name="negotiationtimeout"></a>NegotiationTimeout  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Časový interval, který určuje maximální doba trvání fáze vyjednávání mezi serverem a klientem.  
  
### <a name="reconnecttransportonfailure"></a>ReconnectTransportOnFailure  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, zda připojení pomocí protokolu WS-spolehlivé zasílání zpráv se pokusí znovu připojit po selhání přenosu.  
  
### <a name="replaycachesize"></a>ReplayCacheSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Počet uložené v mezipaměti náhodně generované identifikátory používá pro rozpoznání opětovného přehrání.  
  
### <a name="replaywindow"></a>Třída ReplayWindow  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Časový interval, který určuje dobu, ve kterém jsou platné náhodně generované identifikátory jednotlivé zprávy.  
  
### <a name="sessionkeyrenewalinterval"></a>SessionKeyRenewalInterval  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Časový interval, který určuje dobu, po které může iniciátor obnovuje klíč pro relace zabezpečení.  
  
### <a name="sessionkeyrolloverinterval"></a>SessionKeyRolloverInterval  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Časový interval, který určuje časový interval je klíč předchozí relace při obnovení klíče platná pro příchozí zprávy.  
  
### <a name="timestampvalidityduration"></a>TimestampValidityDuration  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Časový interval, který určuje dobu, ve kterém je platný časové razítko.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>

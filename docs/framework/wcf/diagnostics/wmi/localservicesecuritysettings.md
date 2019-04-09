---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: 15304630eb8a14e01d4815ddddc84cd32796fdcf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133478"
---
# <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings
LocalServiceSecuritySettings  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Logická hodnota určující, zda jsou zjištěny a řešeny automaticky opakované útoky proti kanálu.  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet nevyřešených bezpečnostních relací, které služba podporuje.  
  
### <a name="issuedcookielifetime"></a>IssuedCookieLifetime  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Interval TimeSpan, který určuje životnost vydanou pro všechny nové bezpečnostní soubory cookie.  
  
### <a name="maxcachedcookies"></a>MaxCachedCookies  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet souborů cookie, které lze uložit do mezipaměti.  
  
### <a name="maxclockskew"></a>MaxClockSkew  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Interval TimeSpan, který určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran.  
  
### <a name="maxpendingsessions"></a>MaxPendingSessions  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet nevyřešených připojení služby.  
  
### <a name="maxstatefulnegotiations"></a>MaxStatefulNegotiations  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Počet bezpečnostních vyjednávání, které mohou být souběžně aktivní.  
  
### <a name="negotiationtimeout"></a>NegotiationTimeout  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Interval TimeSpan, který určuje maximální dobu trvání fáze bezpečnostního vyjednávání mezi serverem a klientem.  
  
### <a name="reconnecttransportonfailure"></a>ReconnectTransportOnFailure  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Logická hodnota určující, zda připojení používající posílání WS-Reliable se pokusí znovu připojit po selhání přenosu.  
  
### <a name="replaycachesize"></a>ReplayCacheSize  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Počet elementů v mezipaměti náhodně generované identifikátory použitých pro zjištění opakování.  
  
### <a name="replaywindow"></a>Třída ReplayWindow  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Interval TimeSpan, který určuje dobu, po kterou jsou platné náhodně generované identifikátory jednotlivých zpráv.  
  
### <a name="sessionkeyrenewalinterval"></a>SessionKeyRenewalInterval  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Interval TimeSpan, který určuje dobu, po které iniciátor obnoví klíč relace zabezpečení.  
  
### <a name="sessionkeyrolloverinterval"></a>SessionKeyRolloverInterval  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Časový interval, který určuje časový interval klíč předchozí relace platí na příchozích zprávách během obnovení klíče.  
  
### <a name="timestampvalidityduration"></a>TimestampValidityDuration  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Interval TimeSpan, který určuje dobu, ve kterém je platné časové razítko.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>

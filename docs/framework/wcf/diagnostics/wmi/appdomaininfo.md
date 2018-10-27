---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 0b7f8aadbd9a9dfcdd33fc65be3a5a41ea95f5be
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50170221"
---
# <a name="appdomaininfo"></a>AppDomainInfo
Informace o domény aplikace  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída AppDomainInfo nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída AppDomainInfo má následující vlastnosti:  
  
### <a name="appdomainid"></a>AppDomainId  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Id domény aplikace.  
  
### <a name="isdefault"></a>IsDefault  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Označuje, zda je doména appdomain výchozí.  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  
 Datový typ: boolean  
  
 Přístup k typu: čtení a zápis  
  
 Hodnota, která určuje, zda jsou špatně vytvořené zprávy zaznamenány.  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  
 Datový typ: boolean  
  
 Přístup k typu: čtení a zápis  
  
 Hodnota, která určuje, zda jsou zprávy trasovány na úrovni služby (před šifrování a týkají).  
  
### <a name="logmessagesattransportlevel"></a>LogMessagesAtTransportLevel  
 Datový typ: boolean  
  
 Přístup k typu: čtení a zápis  
  
 Hodnota, která určuje, zda jsou zprávy trasovány na úrovni přenosu.  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  
 Datový typ: TraceListener pole  
  
 Přístup k typu: jen pro čtení  
  
 Kolekce naslouchací procesy trasování, kteří poslouchají zdroj trasování System.Wmi.MessageLogging.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Název domény aplikace.  
  
### <a name="performancecounters"></a>Čítače výkonu  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Rozsah počítačů aktivního výkonu v doméně aplikace.  
  
### <a name="processid"></a>ID procesu  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 ID procesu.  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Cesta ke konfiguraci této služby.  
  
### <a name="tracelevel"></a>TraceLevel  
 Datový typ: řetězec  
  
 Přístup k typu: čtení a zápis  
  
 Úroveň trasování System.Wmi zdroje trasování.  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  
 Datový typ: TraceListener pole  
  
 Přístup k typu: jen pro čtení  
  
 Kolekce naslouchacích procesů trasování zdrojem System.ServiceModel.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|

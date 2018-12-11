---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 0b7f8aadbd9a9dfcdd33fc65be3a5a41ea95f5be
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127079"
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
  
 Typ přístupu: jen pro čtení  
  
 Id domény aplikace.  
  
### <a name="isdefault"></a>IsDefault  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Označuje, zda je doména appdomain výchozí.  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  
 Datový typ: boolean  
  
 Typ přístupu: Čtení/zápisu  
  
 Hodnota, která určuje, zda jsou špatně vytvořené zprávy zaznamenány.  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  
 Datový typ: boolean  
  
 Typ přístupu: Čtení/zápisu  
  
 Hodnota, která určuje, zda jsou zprávy trasovány na úrovni služby (před šifrování a týkají).  
  
### <a name="logmessagesattransportlevel"></a>LogMessagesAtTransportLevel  
 Datový typ: boolean  
  
 Typ přístupu: Čtení/zápisu  
  
 Hodnota, která určuje, zda jsou zprávy trasovány na úrovni přenosu.  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  
 Datový typ: TraceListener pole  
  
 Typ přístupu: jen pro čtení  
  
 Kolekce naslouchací procesy trasování, kteří poslouchají zdroj trasování System.Wmi.MessageLogging.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Název domény aplikace.  
  
### <a name="performancecounters"></a>Čítače výkonu  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Rozsah počítačů aktivního výkonu v doméně aplikace.  
  
### <a name="processid"></a>ID procesu  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 ID procesu.  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Cesta ke konfiguraci této služby.  
  
### <a name="tracelevel"></a>TraceLevel  
 Datový typ: řetězec  
  
 Typ přístupu: Čtení/zápisu  
  
 Úroveň trasování System.Wmi zdroje trasování.  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  
 Datový typ: TraceListener pole  
  
 Typ přístupu: jen pro čtení  
  
 Kolekce naslouchacích procesů trasování zdrojem System.ServiceModel.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|

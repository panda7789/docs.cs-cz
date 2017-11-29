---
title: AppDomainInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 97818cf1fc6fa1c59b8b0eeaab69a73b21360151
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="appdomaininfo"></a>AppDomainInfo
Informace o doméně aplikace  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda domény aplikace je výchozí domény aplikace.  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  
 Datový typ: logická hodnota  
  
 Přístup k typu: čtení/zápisu  
  
 Hodnota, která určuje, zda mají být protokolovány poškozených zpráv.  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  
 Datový typ: logická hodnota  
  
 Přístup k typu: čtení/zápisu  
  
 Hodnota, která určuje, zda jsou zprávy nalezeny na úrovni služby (před šifrování a související přenosu transformací).  
  
### <a name="logmessagesattransportlevel"></a>LogMessagesAtTransportLevel  
 Datový typ: logická hodnota  
  
 Přístup k typu: čtení/zápisu  
  
 Hodnota, která určuje, zda jsou zprávy nalezeny na úrovni přenosu.  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  
 Datový typ: TraceListener pole  
  
 Přístup k typu: jen pro čtení  
  
 Kolekce naslouchací procesy trasování které naslouchání zdroje System.Wmi.MessageLogging trasování.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Název domény aplikace.  
  
### <a name="performancecounters"></a>čítače výkonu  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Rozsah čítače výkonu active do domény aplikace.  
  
### <a name="processid"></a>ID procesu  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 ID procesu  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Cesta ke konfiguraci služby.  
  
### <a name="tracelevel"></a>TraceLevel  
 Datový typ: řetězec  
  
 Přístup k typu: čtení/zápisu  
  
 Úroveň trasování System.Wmi zdroje trasování.  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  
 Datový typ: TraceListener pole  
  
 Přístup k typu: jen pro čtení  
  
 Kolekce ve zdroji System.ServiceModel trasování – moduly naslouchání.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|

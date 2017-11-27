---
title: "Služba"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bd784b470810e16b86ba7537b1f45681ac3e1ed1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="service"></a>Služba
Služba  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída služby nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída služby má následující vlastnosti:  
  
### <a name="baseaddresses"></a>BaseAddresses  
 Datový typ: pole řetězců  
  
 Přístup k typu: jen pro čtení  
  
 Základní adresy používané službou.  
  
### <a name="behaviors"></a>Chování  
 Datový typ: chování pole  
  
 Přístup k typu: jen pro čtení  
  
 Chování, které jsou spojené s touto službou.  
  
### <a name="configurationname"></a>ConfigurationName  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Název instance instance čítače výkonu služby.  
  
### <a name="distinguishedname"></a>DistinguishedName  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Název služby na adrese.  
  
### <a name="extensions"></a>Rozšíření  
 Datový typ: pole řetězců  
  
 Přístup k typu: jen pro čtení  
  
 Kontexty instance pro rozšíření instance služby.  
  
### <a name="metadata"></a>Metadata  
 Datový typ: pole řetězců  
  
 Přístup k typu: jen pro čtení  
  
 Nastavení služby metadat.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Jedinečný název této služby.  
  
### <a name="namespace"></a>Obor názvů  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Obor názvů služby.  
  
### <a name="opened"></a>Otevřít  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Čas, kdy byla služba otevřena.  
  
### <a name="outgoingchannels"></a>OutgoingChannels  
 Datový typ: pole Channel  
  
 Přístup k typu: jen pro čtení  
  
 Kanály, které vycházejí z instance služby.  
  
### <a name="processid"></a>ID procesu  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Id procesu procesu, který je hostitelem služby.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|

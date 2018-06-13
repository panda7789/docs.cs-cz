---
title: Služba
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: 0cfeb178e26f6c93e29210accf5d7866cc1fca02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487144"
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

---
title: Služba
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991442"
---
# <a name="service"></a>Služba
Služba  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 Třídu služby nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třídu služby má následující vlastnosti:  
  
### <a name="baseaddresses"></a>BaseAddresses  
 Datový typ: pole řetězců  
  
 Typ přístupu: jen pro čtení  
  
 Základní adresy používané službou.  
  
### <a name="behaviors"></a>Chování  
 Datový typ: Chování pole  
  
 Typ přístupu: jen pro čtení  
  
 Chování, které jsou spojené s touto službou.  
  
### <a name="configurationname"></a>ConfigurationName  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Instanci název instance čítače výkonu služby.  
  
### <a name="distinguishedname"></a>DistinguishedName  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Název služby na adrese.  
  
### <a name="extensions"></a>Rozšíření  
 Datový typ: pole řetězců  
  
 Typ přístupu: jen pro čtení  
  
 Kontexty instance pro rozšíření instance služby.  
  
### <a name="metadata"></a>Metadata  
 Datový typ: pole řetězců  
  
 Typ přístupu: jen pro čtení  
  
 Nastavení metadat služby.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Jedinečný název této služby.  
  
### <a name="namespace"></a>Obor názvů  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Obor názvů služby.  
  
### <a name="opened"></a>Otevřít  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Čas, kdy byla služba otevřena.  
  
### <a name="outgoingchannels"></a>OutgoingChannels  
 Datový typ: Pole Channel  
  
 Typ přístupu: jen pro čtení  
  
 Kanály, které vycházejí z instance služby.  
  
### <a name="processid"></a>ID procesu  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Proces id procesu, který je hostitelem služby.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|

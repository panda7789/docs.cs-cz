---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 572e458f08c4717207667db9940296c4a957199a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225492"
---
# <a name="servicethrottlingbehavior"></a>ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třídy ServiceThrottlingBehavior nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třídy ServiceThrottlingBehavior má následující vlastnosti:  
  
### <a name="maxconcurrentcalls"></a>MaxConcurrentCalls  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet zpráv aktivně pracujících přes veškeré objekty odesílatele v ServiceHost.  
  
### <a name="maxconcurrentinstances"></a>MaxConcurrentInstances  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet objektů služeb, které můžete provést najednou.  
  
### <a name="maxconcurrentsessions"></a>MaxConcurrentSessions  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet relací, které může hostitel najednou přijmout.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>

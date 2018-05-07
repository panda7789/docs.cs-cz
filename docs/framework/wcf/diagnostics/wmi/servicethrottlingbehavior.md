---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 9a7fbf93dbdbf1a6debcf865b4883b5784e2ff4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="servicethrottlingbehavior"></a>ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída třídy ServiceThrottlingBehavior nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída třídy ServiceThrottlingBehavior má následující vlastnosti:  
  
### <a name="maxconcurrentcalls"></a>maxConcurrentCalls  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet zpráv ve všech objektech dispečera v ServiceHost aktivně zpracovávají.  
  
### <a name="maxconcurrentinstances"></a>maxConcurrentInstances  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet objekty služby, které mohou být prováděny současně.  
  
### <a name="maxconcurrentsessions"></a>maxConcurrentSessions  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet relací, které hostitele může přijmout najednou.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>

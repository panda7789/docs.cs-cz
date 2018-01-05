---
title: "IEnumDefinitionIdentity – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumDefinitionIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumDefinitionIdentity
helpviewer_keywords: IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79e2a35a455407715a05e826d31c5d5ab05a02ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdefinitionidentity-interface"></a>IEnumDefinitionIdentity – rozhraní
Slouží jako enumerátoru pro kolekci `IDefinitionIdentity` objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|Získá ukazatele rozhraní na nový `IEnumDefinitionIdentity` objekt, který obsahuje členy stejné jako to `IEnumDefinitionIdentity`.|  
|`IEnumDefinitionIdentity::Next`|Získá zadaný počet `IDefinitionIdentity` objektů, počínaje na aktuální pozici.|  
|`IEnumDefinitionIdentity::Reset`|Ukazatel instrukce přesune na začátku tohoto `IEnumDefinitionIdentity`.|  
|`IEnumDefinitionIdentity::Skip`|Ukazatel instrukce dál přesune o zadaný počet elementů, počínaje na aktuální pozici.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IDefinitionIdentity – rozhraní](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)

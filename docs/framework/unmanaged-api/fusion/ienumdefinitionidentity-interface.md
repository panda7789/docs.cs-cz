---
title: IEnumDefinitionIdentity – rozhraní
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bbd8476b7778de6d0023f3a8522a44be6626884
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751524"
---
# <a name="ienumdefinitionidentity-interface"></a>IEnumDefinitionIdentity – rozhraní
Slouží jako enumerátoru pro kolekci `IDefinitionIdentity` objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`IEnumDefinitionIdentity::Clone`|Získá ukazatel rozhraní na nový `IEnumDefinitionIdentity` objekt, který obsahuje stejné členy jako to `IEnumDefinitionIdentity`.|  
|`IEnumDefinitionIdentity::Next`|Získá zadaný počet `IDefinitionIdentity` objektů, počínaje na aktuální pozici.|  
|`IEnumDefinitionIdentity::Reset`|Přesune ukazatel na instrukci na začátek `IEnumDefinitionIdentity`.|  
|`IEnumDefinitionIdentity::Skip`|Přesune ukazatele na instrukci vpřed o zadaný počet prvků počínaje od aktuální pozice.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IDefinitionIdentity – rozhraní](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)

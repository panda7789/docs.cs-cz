---
title: IMetaDataTables::GetGuid – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 57df124f15f78daad053d9634e1baa969a65cc35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175275"
---
# <a name="imetadatatablesgetguid-method"></a>IMetaDataTables::GetGuid – metoda
Získá identifikátor GUID z řádku na zadaný index.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ixGuid`  
 [v] Index řádku, ze kterého chcete získat identifikátor GUID.  
  
 `ppGuid`  
 [out] Ukazatel na ukazatel na identifikátor GUID.  
  
## <a name="remarks"></a>Poznámky  

  Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky. Informace o tabulce GUID naleznete v dokumentaci cli (Common Language Infrastructure), zejména "Oddíl II: Definice metadat a sémantika". Dokumentace je k dispozici online; viz [ecma c# a obecné standardy jazykové infrastruktury](../../../standard/components.md#applicable-standards) a [standardní ECMA-335 – common language infrastructure (CLI).](http://www.ecma-international.org/publications/standards/Ecma-335.htm)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataTables – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

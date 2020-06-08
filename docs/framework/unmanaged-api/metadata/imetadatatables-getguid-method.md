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
ms.openlocfilehash: 6f273cb03ad00957afb2bd78fe538a940fae236a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501232"
---
# <a name="imetadatatablesgetguid-method"></a>IMetaDataTables::GetGuid – metoda
Získá identifikátor GUID z řádku na zadaném indexu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ixGuid`  
 pro Index řádku, ze kterého se má získat identifikátor GUID  
  
 `ppGuid`  
 mimo Ukazatel na ukazatel na identifikátor GUID.  
  
## <a name="remarks"></a>Poznámky  

  Nedoporučujeme používat tuto metodu, protože nevrací konzistentní výsledky. Informace o tabulce identifikátorů GUID najdete v dokumentaci k Common Language Infrastructure (CLI), zejména v oddílu oddíl II: definice metadat a sémantika. Dokumentace je k dispozici online; viz [ECMA C# a Common Language Infrastructure standardy](../../../standard/components.md#applicable-standards) a [standardní ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataTables – rozhraní](imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](imetadatatables2-interface.md)

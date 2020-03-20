---
title: IMetaDataTables::GetRow – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177108"
---
# <a name="imetadatatablesgetrow-method"></a>IMetaDataTables::GetRow – metoda
Získá řádek na zadaný řádek indexu, v tabulce v zadaném indexu tabulky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ixTbl`  
 [v] Index tabulky, ze kterého bude řádek načten.  
  
 `rid`  
 [v] Index řádku získat.  
  
 `ppRow`  
 [out] Ukazatel na ukazatel na řádek.  
  
## <a name="remarks"></a>Poznámky  

  Nedoporučujeme použití této metody, protože nevrací konzistentní výsledky. Informace o tabulce GUID naleznete v dokumentaci cli (Common Language Infrastructure), zejména "Oddíl II: Definice metadat a sémantika". Dokumentace je k dispozici online; viz [ecma c# a obecné standardy jazykové infrastruktury](../../../standard/components.md#applicable-standards) a [standardní ECMA-335 – common language infrastructure (CLI).](http://www.ecma-international.org/publications/standards/Ecma-335.htm)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataTables – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

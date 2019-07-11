---
title: IMetaDataDispenser::OpenScopeOnMemory – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 204e5660e95434f8d0c44d54f4fdbb1c2acc1e5d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777782"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a>IMetaDataDispenser::OpenScopeOnMemory – metoda
Otevře se oblast paměti, která obsahuje existující metadata. To znamená, že tato metoda otevře oblastí paměti, ve kterém existujících dat je považován za metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pData`  
 [in] Ukazatel, který určuje počáteční adresu oblasti paměti.  
  
 `cbData`  
 [in] Velikost oblasti paměti v bajtech.  
  
 `dwOpenFlags`  
 [in] Hodnota [coropenflags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčtu pro určení režimu (čtení, zápisu a tak dále) pro otevření.  
  
 `riid`  
 [in] Identifikátor IID rozhraní požadované metadat má být vrácen. volající budou používat rozhraní pro import (čtení) nebo generování metadat (zápis).  
  
 Hodnota `riid` musíte zadat jedno z rozhraní "import" nebo "generování". Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [out] Ukazatel na vrácené rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Kopie v paměti metadat může být dotázán pomocí metody z jednoho z rozhraní "import" nebo přidat do pomocí metod od rozhraní "generování".  
  
 `OpenScopeOnMemory` Metoda je podobná [imetadatadispenser::openscope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metody, s tím rozdílem, že metadata zájmu již existuje v paměti, nikoli v souboru na disku.  
  
 Pokud cílové oblasti paměti neobsahuje metadata common language runtime (CLR), `OpenScopeOnMemory` metoda se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

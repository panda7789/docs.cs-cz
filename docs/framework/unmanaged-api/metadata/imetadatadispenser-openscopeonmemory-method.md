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
ms.openlocfilehash: 69e5e05012d2b44a76a986591ec990f66bf8ae20
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007322"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a>IMetaDataDispenser::OpenScopeOnMemory – metoda
Otevře oblast paměti, která obsahuje existující metadata. To znamená, že tato metoda otevře zadanou oblast paměti, ve které jsou stávající data považována za metadata.  
  
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
 pro Ukazatel, který určuje počáteční adresu oblasti paměti.  
  
 `cbData`  
 pro Velikost oblasti paměti (v bajtech).  
  
 `dwOpenFlags`  
 pro Hodnota výčtu [CorOpenFlags –](coropenflags-enumeration.md) , která určuje režim (čtení, zápis a tak dále) pro otevření.  
  
 `riid`  
 pro Identifikátor IID požadovaného rozhraní metadat, které má být vráceno; Volající použije rozhraní k importu (čtení) nebo generování (zápisu) metadat.  
  
 Hodnota `riid` musí určovat jedno z rozhraní "Import" nebo "Emit". Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.  
  
 `ppIUnk`  
 mimo Ukazatel na vrácené rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Kopie metadat v paměti se dá dotazovat pomocí metod z jednoho z rozhraní "Import" nebo přidat k použití metod z rozhraní typu "Emit".  
  
 `OpenScopeOnMemory`Metoda je podobná metodě [IMetaDataDispenser:: OpenScope –](imetadatadispenser-openscope-method.md) s tím rozdílem, že metadata zájmu již existují v paměti, nikoli v souboru na disku.  
  
 Pokud cílová oblast paměti neobsahuje metadata modulu CLR (Common Language Runtime), `OpenScopeOnMemory` metoda se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataDispenser – rozhraní](imetadatadispenser-interface.md)
- [IMetaDataDispenserEx – rozhraní](imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport – rozhraní](imetadataassemblyimport-interface.md)
- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)

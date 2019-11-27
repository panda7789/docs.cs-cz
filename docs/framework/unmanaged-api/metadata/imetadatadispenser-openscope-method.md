---
title: IMetaDataDispenser::OpenScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: 5ce1af82631531f8f7105fbf92ba78db3cca437b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442325"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope – metoda
Otevře existující soubor na disku a namapuje jeho metadata do paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szScope`  
 pro Název souboru, který se má otevřít Soubor musí obsahovat metadata modulu CLR (Common Language Runtime).  
  
 `dwOpenFlags`  
 pro Hodnota výčtu [CorOpenFlags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) , která určuje režim (čtení, zápis a tak dále) pro otevření.  
  
 `riid`  
 pro Identifikátor IID požadovaného rozhraní metadat, které má být vráceno; Volající použije rozhraní k importu (čtení) nebo generování (zápisu) metadat.  
  
 Hodnota `riid` musí určovat jedno z rozhraní "Import" nebo "Emit". Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.  
  
 `ppIUnk`  
 mimo Ukazatel na vrácené rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Kopie metadat v paměti se dá dotazovat pomocí metod z jednoho z rozhraní "Import" nebo přidat k použití metod z rozhraní typu "Emit".  
  
 Pokud cílový soubor neobsahuje metadata CLR, metoda `OpenScope` se nezdaří.  
  
 Pokud je v .NET Framework verze 1,0 a verze 1,1, je v případě, že je obor otevřený s `dwOpenFlags` nastaveným na ofRead, nárok na sdílení. To znamená, že pokud následná volání `OpenScope` přejdou na název souboru, který byl dříve otevřen, existující obor je znovu použit a nová sada datových struktur není vytvořena. V důsledku tohoto sdílení ale může dojít k problémům.  
  
 V .NET Framework verze 2,0 se už nesdílí obory otevřené pomocí `dwOpenFlags` nastavené na ofRead. K povolení sdílení oboru použijte hodnotu ofReadOnly. Při sdílení oboru nebudou dotazy, které používají rozhraní metadat pro čtení a zápis, selžou.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

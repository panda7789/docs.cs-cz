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
ms.openlocfilehash: 5185fb6663910c85ce5dae1225b9b10c5dd8bb28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175938"
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
 [v] Název souboru, který má být otevřen. Soubor musí obsahovat metadata clr (COMMON Language runtime).  
  
 `dwOpenFlags`  
 [v] Hodnota [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčtu určit režim (čtení, zápis a tak dále) pro otevření.  
  
 `riid`  
 [v] IID požadované rozhraní metadat, které mají být vráceny; volající použije rozhraní k importu (čtení) nebo vyzařování (zápisu) metadat.  
  
 Hodnota `riid` musí určit jedno z rozhraní "import" nebo "emit". Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [out] Ukazatel na vrácené rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Kopie metadat v paměti může být dotazován pomocí metod z jednoho z rozhraní "import" nebo přidány pomocí metody z jednoho z rozhraní "emit".  
  
 Pokud cílový soubor neobsahuje metadata CLR, `OpenScope` metoda se nezdaří.  
  
 V rozhraní .NET Framework verze 1.0 a verze 1.1, pokud je obor otevřen s `dwOpenFlags` nastavenou na Read, je způsobilý pro sdílení. To znamená, že `OpenScope` pokud následné volání předat název souboru, který byl dříve otevřen, existující obor je znovu použit a není vytvořena nová sada datových struktur. V důsledku tohoto sdílení však mohou vzniknout problémy.  
  
 V rozhraní .NET Framework verze 2.0 `dwOpenFlags` obory otevřené s nastavenou na Read již nejsou sdíleny. Použijte ofReadOnly hodnotu povolit obor, který má být sdílen. Při sdílení oboru se nezdaří dotazy, které používají metadata rozhraní pro čtení a zápis.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

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
ms.openlocfilehash: 8d9de753f1c44338a96e990def80643d591f2a8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007465"
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
 pro Hodnota výčtu [CorOpenFlags –](coropenflags-enumeration.md) , která určuje režim (čtení, zápis a tak dále) pro otevření.  
  
 `riid`  
 pro Identifikátor IID požadovaného rozhraní metadat, které má být vráceno; Volající použije rozhraní k importu (čtení) nebo generování (zápisu) metadat.  
  
 Hodnota `riid` musí určovat jedno z rozhraní "Import" nebo "Emit". Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.  
  
 `ppIUnk`  
 mimo Ukazatel na vrácené rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Kopie metadat v paměti se dá dotazovat pomocí metod z jednoho z rozhraní "Import" nebo přidat k použití metod z rozhraní typu "Emit".  
  
 Pokud cílový soubor neobsahuje metadata CLR, `OpenScope` metoda se nezdaří.  
  
 Pokud je v .NET Framework verze 1,0 a verze 1,1, je v případě otevření oboru s `dwOpenFlags` nastavením na ofRead nárok na sdílení. To znamená, že pokud následná volání `OpenScope` přejdoucí na název souboru, který byl dříve otevřen, existující obor je znovu použit a nová sada datových struktur není vytvořena. V důsledku tohoto sdílení ale může dojít k problémům.  
  
 V .NET Framework verze 2,0 již nejsou obory otevřené s `dwOpenFlags` nastavenou na ofRead nadále sdíleny. K povolení sdílení oboru použijte hodnotu ofReadOnly. Při sdílení oboru nebudou dotazy, které používají rozhraní metadat pro čtení a zápis, selžou.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
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

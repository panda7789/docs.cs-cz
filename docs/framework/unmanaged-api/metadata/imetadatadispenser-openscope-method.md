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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0fb805e3292d90fd5f9562d9b0b8fcc31f84ec7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope – metoda
Otevře existujícího souboru na disku a mapuje jeho metadata do paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szScope`  
 [v] Název souboru, který se otevřít. Soubor musí obsahovat běžná metadata language runtime (CLR).  
  
 `dwOpenFlags`  
 [v] Hodnota [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčtu pro otevírání zadejte režim (čtení, zápisu a tak dále).  
  
 `riid`  
 [v] Identifikátory IID rozhraní požadované metadata má být vrácen. volající se použít rozhraní pro import (čtení) nebo emitování metadata (zápisu).  
  
 Hodnota `riid` musíte zadat jednu z "import" nebo "emitování" rozhraní. Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [out] Ukazatel rozhraní vrácená.  
  
## <a name="remarks"></a>Poznámky  
 Kopie v paměti metadat můžete položit dotaz na metodami z jednoho z rozhraní "import", nebo přidat do pomocí metod od verze rozhraní "emitování".  
  
 Pokud cílový soubor neobsahuje CLR metadata `OpenScope` metoda se nezdaří.  
  
 V rozhraní .NET Framework verze 1.0 a 1.1, pokud obor je otevřen s `dwOpenFlags` nastavení ofRead, je vhodné pro sdílení. To znamená pokud následných volání `OpenScope` průchodu názvu souboru, který byl dříve otevřen, se znovu použije stávající oboru a novou sadu datové struktury nebyl vytvořen. Problémy se však, může dojít z důvodu této sdílení.  
  
 V rozhraní .NET Framework verze 2.0, otevřené obory se `dwOpenFlags` nastaven na ofRead jsou již sdíleny. Použijte hodnotu ofReadOnly umožňující oboru ke sdílení. Pokud je sdílen obor, dotazy, které používají "pro čtení a zápis" rozhraní metadat se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

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
ms.openlocfilehash: 5b94987631f7dbbe39e585a8ea2c2252b9427613
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079601"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope – metoda
Otevření existujícího souboru na disku a mapuje jeho metadata do paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szScope`  
 [in] Název souboru, který má být otevřen. Soubor musí obsahovat metadata common language runtime (CLR).  
  
 `dwOpenFlags`  
 [in] Hodnota [coropenflags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčtu pro určení režimu (čtení, zápisu a tak dále) pro otevření.  
  
 `riid`  
 [in] Identifikátor IID rozhraní požadované metadat má být vrácen. volající budou používat rozhraní pro import (čtení) nebo generování metadat (zápis).  
  
 Hodnota `riid` musíte zadat jedno z rozhraní "import" nebo "generování". Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [out] Ukazatel na vrácené rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Kopie v paměti metadat může být dotázán pomocí metody z jednoho z rozhraní "import" nebo přidat do pomocí metod od rozhraní "generování".  
  
 Pokud cílový soubor neobsahuje metadat CLR `OpenScope` metoda se nezdaří.  
  
 V rozhraní .NET Framework verze 1.0 a 1.1, pokud obor se otevře s `dwOpenFlags` nastavíte ofRead, je vhodné pro sdílení. To znamená pokud následných volání `OpenScope` předat mu název souboru, který byl dříve otevřen, existující obor již byl použit a není vytvořena nová sada datových struktur. Však mohou vzniknout problémy, kvůli toto sdílení.  
  
 V rozhraní .NET Framework verze 2.0, otevřeného oborů s `dwOpenFlags` nastavenou na ofRead jsou již sdíleny. Hodnota ofReadOnly slouží k povolení oboru, který má být sdílené. Při sdílení obor dotazů, které používají "pro čtení a zápisu" rozhraní metadat se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
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

---
title: IMetaDataDispenserEx – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96475086b1244ae75ed692dd10cb693af0be9af7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186950"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx – rozhraní
Rozšiřuje [imetadatadispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) rozhraní poskytnout možnost řídit, jak použít metadat rozhraní API pro aktuální obor metadat.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[FindAssembly – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|Tato metoda není implementována. Pokud je volána, vrátí E_NOTIMPL.|  
|[FindAssemblyModule – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|Tato metoda není implementována. Pokud je volána, vrátí E_NOTIMPL.|  
|[GetCORSystemDirectory – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Získá adresář, který obsahuje aktuální modul (CLR). Tato metoda je podporována pouze pro použití ladicími mimo proces. Pokud je volána z jiné součásti, vrátí E_NOTIMPL.|  
|[GetOption – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Získá hodnotu zadané možnosti pro aktuální obor metadat. Možnost řídí, jak se zpracovává volání na aktuální metadat.|  
|[OpenScopeOnITypeInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|Tato metoda není implementována. Pokud je volána, vrátí E_NOTIMPL.|  
|[SetOption – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Nastaví zadanou možnost dané hodnotě pro aktuální obor metadat. Možnost řídí, jak se zpracovává volání na aktuální metadat.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

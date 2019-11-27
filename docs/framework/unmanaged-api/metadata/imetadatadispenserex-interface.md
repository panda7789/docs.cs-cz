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
ms.openlocfilehash: 985cdea670714394119fb846e9e55a01713559a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431142"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx – rozhraní
Rozšiřuje rozhraní [rozhraní IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) , aby poskytovala schopnost řídit způsob, jakým rozhraní API metadat pracují v aktuálním oboru metadat.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[FindAssembly – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|Tato metoda není implementována. Při volání Vrátí E_NOTIMPL.|  
|[FindAssemblyModule – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|Tato metoda není implementována. Při volání Vrátí E_NOTIMPL.|  
|[GetCORSystemDirectory – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Načte adresář, který obsahuje aktuální modul CLR (Common Language Runtime). Tato metoda je podporována pouze pro použití vnitroprocesové ladicí program. Pokud se volá z jiné součásti, vrátí E_NOTIMPL.|  
|[GetOption – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Získá hodnotu zadané možnosti pro aktuální obor metadat. Možnost určuje, jak jsou zpracovávány volání do aktuálního oboru metadat.|  
|[OpenScopeOnITypeInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|Tato metoda není implementována. Při volání Vrátí E_NOTIMPL.|  
|[SetOption – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Nastaví zadanou možnost na danou hodnotu pro aktuální obor metadat. Možnost určuje, jak jsou zpracovávány volání do aktuálního oboru metadat.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

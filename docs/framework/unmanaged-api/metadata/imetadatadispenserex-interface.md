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
ms.openlocfilehash: 96f0c0c254ce255581ac2937c805096918ab29e8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008050"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx – rozhraní
Rozšiřuje rozhraní [rozhraní IMetaDataDispenser](imetadatadispenser-interface.md) , aby poskytovala schopnost řídit způsob, jakým rozhraní API metadat pracují v aktuálním oboru metadat.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[FindAssembly – metoda](imetadatadispenserex-findassembly-method.md)|Tato metoda není implementována. Při volání Vrátí E_NOTIMPL.|  
|[FindAssemblyModule – metoda](imetadatadispenserex-findassemblymodule-method.md)|Tato metoda není implementována. Při volání Vrátí E_NOTIMPL.|  
|[GetCORSystemDirectory – metoda](imetadatadispenserex-getcorsystemdirectory-method.md)|Načte adresář, který obsahuje aktuální modul CLR (Common Language Runtime). Tato metoda je podporována pouze pro použití vnitroprocesové ladicí program. Pokud se volá z jiné součásti, vrátí E_NOTIMPL.|  
|[GetOption – metoda](imetadatadispenserex-getoption-method.md)|Získá hodnotu zadané možnosti pro aktuální obor metadat. Možnost určuje, jak jsou zpracovávány volání do aktuálního oboru metadat.|  
|[OpenScopeOnITypeInfo – metoda](imetadatadispenserex-openscopeonitypeinfo-method.md)|Tato metoda není implementována. Při volání Vrátí E_NOTIMPL.|  
|[SetOption – metoda](imetadatadispenserex-setoption-method.md)|Nastaví zadanou možnost na danou hodnotu pro aktuální obor metadat. Možnost určuje, jak jsou zpracovávány volání do aktuálního oboru metadat.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro metadata](metadata-interfaces.md)
- [IMetaDataDispenser – rozhraní](imetadatadispenser-interface.md)
- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataImport – rozhraní](imetadataimport-interface.md)

---
title: "IMetaDataDispenserEx – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx
helpviewer_keywords: IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5ecb4e94c0deed3ed62b2d2eb8b0309ca092abf8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx – rozhraní
Rozšiřuje [imetadatadispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) rozhraní poskytovat funkce řídit, jak pracovat metadat rozhraní API v aktuálním oboru metadat.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Findassembly – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|Tato metoda není implementována. Pokud je volána, vrátí E_NOTIMPL.|  
|[Findassemblymodule – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|Tato metoda není implementována. Pokud je volána, vrátí E_NOTIMPL.|  
|[Getcorsystemdirectory – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Získá adresář, který obsahuje modul aktuální CLR (CLR). Tato metoda podporuje jenom pro použití ladicí programy mimo proces. Pokud volání z jiné komponenty, vrátí E_NOTIMPL.|  
|[Getoption – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Získá hodnotu Zadaná možnost pro aktuální obor metadat. Možnost určuje způsob zpracování volání do aktuálního oboru metadat.|  
|[Openscopeonitypeinfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|Tato metoda není implementována. Pokud je volána, vrátí E_NOTIMPL.|  
|[SetOption – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Nastaví Zadaná možnost zadanou hodnotu pro aktuální obor metadat. Možnost určuje způsob zpracování volání do aktuálního oboru metadat.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Imetadatadispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [Imetadataemit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Imetadataimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

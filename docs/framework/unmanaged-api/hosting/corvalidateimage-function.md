---
title: "_CorValidateImage – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 03deb62a84a1e9c6cee898fe0023c34b8c538ece
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corvalidateimage-function"></a>_CorValidateImage – funkce
Ověří spravovaný modul bitové kopie a po nějaké době načíst upozorní zavaděč operačního systému.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ImageBase`  
 [v] Ukazatel na počáteční umístění bitové kopie k ověření jako spravovaný kód. Obrázek musí již načten do paměti.  
  
 `FileName`  
 [v] Název souboru obrázku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato funkce vrátí standardní hodnoty `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, a `E_FAIL`, a také následující hodnoty.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Bitovou kopii je neplatný. Tato hodnota má HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|Obrázek je platný. Tato hodnota má HRESULT 0x00000000L.|  
  
## <a name="remarks"></a>Poznámky  
 V systému Windows XP a novějších verzích kontroluje zavaděč operačního systému pro spravované moduly zkoumáním bit COM popisovač Directory společné hlavičky objekt souboru formátu (COFF). Sada bit označuje spravovaný modul. Pokud zavaděč zjistí spravovaný modul, načte MsCorEE.dll a volání `_CorValidateImage`, který provede následující akce:  
  
-   Potvrdí, že bitová kopie je platný spravovaný modul.  
  
-   Vstupní bod v common language runtime (CLR) se změní vstupní bod v bitové kopii.  
  
-   Pro 64bitové verze systému Windows upraví bitovou kopii, která je v paměti pomocí transformace z PE32 na PE32 + formát.  
  
-   Vrátí k zavaděč, když jsou načíst spravovaný modul bitové kopie.  
  
 Pro spustitelné bitové kopie operačního systému zavaděč pak zavolá [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) funkce, bez ohledu na to, vstupní bod uvedený v spustitelný soubor. Pro knihovny DLL sestavení Image, zavaděč volá [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkce.  
  
 `_CorExeMain`nebo `_CorDllMain` provede následující akce:  
  
-   Inicializuje modulu CLR.  
  
-   Vyhledá spravovaný vstupní bod z hlavičky sestavení CLR.  
  
-   Zahájí spuštění.  
  
 Zavaděč volání [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) funkce při správě modulu Image jsou odpojen. Tato funkce ale neprovede žádnou akci; právě vrátí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

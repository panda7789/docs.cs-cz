---
title: _CorValidateImage – funkce
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a84869281ec27aface96d722603186382c6e15e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730773"
---
# <a name="corvalidateimage-function"></a>_CorValidateImage – funkce
Ověřuje bitové kopie spravovaného modulu a upozorní zavaděč operačního systému po jejich načtení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ImageBase`  
 [in] Ukazatel na počáteční umístění image se ověřit jako spravovaný kód. Na obrázku musí být již načtena do paměti.  
  
 `FileName`  
 [in] Název souboru obrázku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato funkce vrací standardní hodnoty `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, a `E_FAIL`, a také následující hodnoty.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Na obrázku je neplatný. Tato hodnota nemá HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|Na obrázku je platný. Tato hodnota nemá HRESULT 0x00000000L.|  
  
## <a name="remarks"></a>Poznámky  
 Ve Windows XP a novějších verzích ověřuje zavaděč operačního systému pro spravované moduly kontrolou bitu COM popisovač adresáře v společné hlavičky objektu file format (COFF). Sada bit označuje spravovaný modul. Pokud zavaděč odhalí spravovaný modul, načtení MsCorEE.dll a volání `_CorValidateImage`, který provede následující akce:  
  
-   Potvrzuje se tím, že bitová kopie je platný spravovaný modul.  
  
-   Změní vstupní bod v bitové kopii na vstupní bod v modulu common language runtime (CLR).  
  
-   Pro 64bitové verze systému Windows upraví obrázek, který je v paměti její transformací z formátu PE32 na formát PE32 +.  
  
-   Vrátí zavaděč, když jsou bitové kopie spravovaného modulu načteny.  
  
 Pro spustitelné bitové kopie na zavaděči operačního systému pak zavolá [Funkce _CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) funkce bez ohledu na vstupní bod uvedený ve spustitelném souboru. Pro bitové kopie sestavení knihovny DLL, volání zavaděče [_cordllmain –](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkce.  
  
 `_CorExeMain` nebo `_CorDllMain` provede následující akce:  
  
-   Inicializuje modul CLR.  
  
-   Vyhledá spravovaný vstupní bod v záhlaví modulu CLR sestavení.  
  
-   Zahájí vykonávání.  
  
 Volání zavaděče [_corimageunloading –](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) fungovat v případě, že spravované bitové kopie modulu jsou uvolněna. Tato funkce ale neprovede žádnou akci; právě vrátí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

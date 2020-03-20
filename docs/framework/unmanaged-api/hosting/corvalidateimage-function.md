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
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178219"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage – funkce
Ověří image spravovaného modulu a upozorní zavaděč operačního systému po jejich načtení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ImageBase`  
 [v] Ukazatel na počáteční umístění bitové kopie k ověření jako spravovaný kód. Obraz již musí být načten do paměti.  
  
 `FileName`  
 [v] Název souboru obrázku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato funkce vrátí `E_INVALIDARG`standardní `E_OUTOFMEMORY` `E_UNEXPECTED`hodnoty `E_FAIL`, , a , stejně jako následující hodnoty.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Obrázek je neplatný. Tato hodnota má HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|Obrázek je platný. Tato hodnota má HRESULT 0x00000000L.|  
  
## <a name="remarks"></a>Poznámky  
 V systému Windows XP a novějších verzích zavaděč operačního systému kontroluje spravované moduly kontrolou bitu adresáře popisovače COM v hlavičce coff (Common object file format). Bit sady označuje spravovaný modul. Pokud zavaděč detekuje spravovaný modul, načte soubor `_CorValidateImage`MsCorEE.dll a zavolá , který provede následující akce:  
  
- Potvrzuje, že bitová kopie je platný spravovaný modul.  
  
- Změní vstupní bod v obraze na vstupní bod v zaběhu společného jazyka (CLR).  
  
- U 64bitových verzí systému Windows upravuje bitovou kopii, která je v paměti, transformací z formátu PE32 na formát PE32+.  
  
- Vrátí se do zavaděče při načtení bitové kopie spravovaného modulu.  
  
 U spustitelných bitových kopií pak zavaděč operačního systému volá [funkci _CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) bez ohledu na vstupní bod zadaný ve spustitelném souboru. Pro obrazy sestavení DLL zavaděč volá [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkci.  
  
 `_CorExeMain`nebo `_CorDllMain` provede následující akce:  
  
- Inicializuje CLR.  
  
- Vyhledá spravovaný vstupní bod z hlavičky CLR sestavení.  
  
- Začíná poprava.  
  
 Zavaděč volá [funkci _CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) při uvolnění bitových kopií spravovaného modulu. Tato funkce však neprovede žádnou akci; to prostě vrátí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

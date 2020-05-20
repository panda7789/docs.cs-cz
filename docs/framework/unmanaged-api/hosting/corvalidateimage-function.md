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
ms.openlocfilehash: 8841fab0517353849ef99594bcbd03dda772c766
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616499"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage – funkce
Ověří bitové kopie spravovaného modulu a upozorní zavaděče operačního systému poté, co byly načteny.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ImageBase`  
 pro Ukazatel na počáteční umístění obrázku, který se má ověřit jako spravovaný kód. Bitová kopie již musí být načtena do paměti.  
  
 `FileName`  
 pro Název souboru obrázku  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato funkce vrací standardní hodnoty `E_INVALIDARG` ,, `E_OUTOFMEMORY` `E_UNEXPECTED` a, a `E_FAIL` také následující hodnoty.  
  
|Vrácená hodnota|Popis|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Obrázek je neplatný. Tato hodnota má hodnotu HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|Bitová kopie je platná. Tato hodnota má HRESULT 0x00000000.|  
  
## <a name="remarks"></a>Poznámky  
 V systému Windows XP a novějších verzích zavaděč operačního systému kontroluje spravované moduly kontrolou adresáře popisovače COM v hlavičce souboru. Sada bitů označuje spravovaný modul. Pokud zavaděč zjistí spravovaný modul, načte MsCorEE. dll a volání `_CorValidateImage` , který provede následující akce:  
  
- Potvrdí, že obrázek je platný spravovaný modul.  
  
- Změní vstupní bod v obrázku na vstupní bod v modulu CLR (Common Language Runtime).  
  
- Pro 64 verze Windows upraví image, která je v paměti, díky transformaci z PE32 na PE32 + Format.  
  
- Vrátí se zavaděč při načtení imagí spravovaného modulu.  
  
 U spustitelných imagí zavaděč operačního systému pak zavolá funkci [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) bez ohledu na vstupní bod zadaný ve spustitelném souboru. Pro Image sestavení DLL volá zavaděč funkci [_CorDllMain](cordllmain-function.md) .  
  
 `_CorExeMain`nebo `_CorDllMain` provede následující akce:  
  
- Inicializuje modul CLR.  
  
- Vyhledá spravovaný vstupní bod ze záhlaví CLR sestavení.  
  
- Zahájí provádění.  
  
 Zavaděč volá funkci [_CorImageUnloading](corimageunloading-function.md) , když jsou bitové kopie spravovaného modulu uvolněny. Tato funkce ale neprovede žádnou akci. pouze vrátí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Globální statické funkce pro metadata](../metadata/metadata-global-static-functions.md)

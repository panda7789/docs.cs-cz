---
title: StrongNameGetBlobFromImage – funkce
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
ms.openlocfilehash: 41226cd909900bd2da7bdcf9b9a49567d3042b01
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094881"
---
# <a name="strongnamegetblobfromimage-function"></a>StrongNameGetBlobFromImage – funkce
Načte binární reprezentaci image sestavení v zadané adrese paměti.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameGetBlobFromImage –](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbBase`  
 pro Adresa paměti namapovaného manifestu sestavení.  
  
 `dwLength`  
 pro Velikost bitové kopie v bajtech v `pbBase`.  
  
 `pbBlob`  
 pro Vyrovnávací paměť obsahující binární reprezentaci obrázku.  
  
 `pcbBlob`  
 [in, out] Požadovaná maximální velikost v bajtech `pbBlob`. Po návratu se skutečná velikost `pbBlob`v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` po úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud se funkce `StrongNameGetBlobFromImage` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameGetBlobFromImage – metoda](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [StrongNameGetBlob – metoda](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

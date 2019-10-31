---
title: StrongNameGetBlob – funkce
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
ms.openlocfilehash: e99346ecca651346b46c220a5e427cbc7f4c4697
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095014"
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob – funkce
Vyplní zadanou vyrovnávací paměť binární reprezentací spustitelného souboru na zadané adrese.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameGetBlob –](../hosting/iclrstrongname-strongnamegetblob-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 pro Platná cesta ke spustitelnému souboru, který se má načíst.  
  
 `pbBlob`  
 pro Vyrovnávací paměť, do které se má načíst spustitelný soubor.  
  
 `pcbBlob`  
 [in, out] Požadovaná maximální velikost v bajtech `pbBlob`. Po návratu se skutečná velikost `pbBlob`v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` po úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud se funkce `StrongNameGetBlob` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameGetBlob – metoda](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [StrongNameGetBlobFromImage – metoda](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

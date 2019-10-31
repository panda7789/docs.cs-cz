---
title: GetHashFromFile – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
ms.openlocfilehash: ffa25b1ec6fda80099f333c1d0a4cf57b76379e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140687"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile – funkce
Vygeneruje hodnotu hash přes obsah zadaného souboru.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: GetHashFromFile –](../hosting/iclrstrongname-gethashfromfile-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szFilePath`  
 pro Název souboru, na který se má vypočítat hodnota hash  
  
 `piHashAlg`  
 [in, out] Algoritmus, který má být použit při generování hodnoty hash. Platné algoritmy jsou definovány rozhraním Win32 CryptoAPI. Je-li `piHashAlg` nastavena na hodnotu 0, je použit výchozí algoritmus CALG_SHA-1.  
  
 `pbHash`  
 mimo Bajtové pole obsahující vygenerovanou hodnotu hash.  
  
 `cchHash`  
 pro Maximální velikost vyrovnávací paměti, na kterou `pbHash` odkazuje.  
  
 `pchHash`  
 mimo Velikost vrácených `pbHash`v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je stejná jako [GetHashFromFileW –](gethashfromfilew-function.md)s tím rozdílem, že specifikace názvu souboru je ANSI namísto Unicode.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetHashFromFile – metoda](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW – metoda](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

---
title: GetHashFromFileW – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
ms.openlocfilehash: db6f39119d143d27c0d3a80a9c65565d4dfd0d39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140671"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW – funkce
Vygeneruje hodnotu hash přes obsah souboru určeného řetězcem Unicode.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: GetHashFromFileW –](../hosting/iclrstrongname-gethashfromfilew-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 pro Název Unicode souboru, na který se má vypočítat hodnota hash  
  
 `piHashAlg`  
 [in, out] Algoritmus, který má být použit při generování hodnoty hash. Platné algoritmy jsou definovány rozhraním Win32 CryptoAPI. Je-li `piHashAlg` nastavena na hodnotu 0, je použit výchozí algoritmus CALG_SHA-1.  
  
 `pbHash`  
 mimo Bajtové pole obsahující vygenerovanou hodnotu hash.  
  
 `cchHash`  
 pro Maximální velikost vyrovnávací paměti, na kterou ukazuje `pbHash`.  
  
 `pchHash`  
 mimo Velikost `pbHash`v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je stejná jako [GetHashFromFile –](gethashfromfile-function.md)s tím rozdílem, že specifikace názvu souboru je Unicode namísto ANSI.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetHashFromFileW – metoda](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile – metoda](../hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

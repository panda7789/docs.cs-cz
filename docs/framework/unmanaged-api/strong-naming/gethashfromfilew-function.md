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
ms.openlocfilehash: 9db583c7064cb910b29e84437f31143dac0d3ec9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175080"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW – funkce
Generuje hash nad obsahem souboru určeného řetězcem Unicode.  
  
 Tato funkce byla zastaralá. Místo toho použijte metodu [ICLRStrongName::GetHashFromFileW.](../hosting/iclrstrongname-gethashfromfilew-method.md)  
  
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
 [v] Název unicode souboru hash.  
  
 `piHashAlg`  
 [dovnitř, ven] Algoritmus, který se má použít při generování algoritmu hash. Platné algoritmy jsou ty, které jsou definovány Win32 CryptoAPI. Pokud `piHashAlg` je nastavena na hodnotu 0, použije se výchozí algoritmus CALG_SHA-1.  
  
 `pbHash`  
 [out] Bajtový pole obsahující vygenerovaný hash.  
  
 `cchHash`  
 [v] Maximální velikost vyrovnávací paměti, `pbHash`na kterou se vztahuje .  
  
 `pchHash`  
 [out] Velikost v bajtů `pbHash`.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je stejná jako [GetHashFromFile](gethashfromfile-function.md), s tím rozdílem, že specifikace názvu souboru je Unicode místo ANSI.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetHashFromFileW – metoda](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile – metoda](../hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

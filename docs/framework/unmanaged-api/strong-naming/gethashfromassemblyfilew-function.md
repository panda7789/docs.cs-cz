---
title: GetHashFromAssemblyFileW – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
ms.openlocfilehash: cf7667f0f2a0f77cd793e00a5de8b030b0c53ec8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140696"
---
# <a name="gethashfromassemblyfilew-function"></a>GetHashFromAssemblyFileW – funkce
Načte hodnotu hash zadaného souboru sestavení pomocí zadaného algoritmu hash. Cesta k souboru sestavení musí být zadána jako řetězec Unicode.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: gethashfromassemblyfilew –](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 pro Cesta k souboru, který se má vyhodnotit Tento parametr musí být řetězec Unicode.  
  
 `piHashAlg`  
 [in, out] Konstanta, která určuje algoritmus hash. Pro výchozí algoritmus hash použijte nulu.  
  
 `pbHash`  
 mimo Vrácená vyrovnávací paměť hash.  
  
 `cchHash`  
 pro Požadovaná maximální velikost `pbHash`.  
  
 `pchHash`  
 mimo Vrácená velikost (v bajtech) `pbHash`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetHashFromAssemblyFileW – metoda](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [GetHashFromAssemblyFile – metoda](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

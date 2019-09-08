---
title: GetHashFromAssemblyFile – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f984d44d0a8acb85562a58653dfd2882053a0ce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799285"
---
# <a name="gethashfromassemblyfile-function"></a>GetHashFromAssemblyFile – funkce
Načte hodnotu hash zadaného souboru sestavení pomocí zadaného algoritmu hash.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: GetHashFromAssemblyFile –](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szFilePath`  
 pro Cesta k souboru, který se má vyhodnotit  
  
 `piHashAlg`  
 [in, out] Konstanta, která určuje algoritmus hash. Pro výchozí algoritmus hash použijte nulu.  
  
 `pbHash`  
 mimo Vrácená vyrovnávací paměť hash.  
  
 `cchHash`  
 pro Požadovaná maximální velikost `pbHash`.  
  
 `pchHash`  
 mimo Vrácená velikost (v bajtech `pbHash`).  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** StrongName. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetHashFromAssemblyFile – metoda](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [GetHashFromAssemblyFileW – metoda](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

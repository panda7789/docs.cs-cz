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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e79c1d89d767832022d487681e0515e5e92a7f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799215"
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
 [in, out] Algoritmus, který má být použit při generování hodnoty hash. Platné algoritmy jsou definovány rozhraním Win32 CryptoAPI. Pokud `piHashAlg` je nastavená na 0, použije se výchozí algoritmus CALG_SHA-1.  
  
 `pbHash`  
 mimo Bajtové pole obsahující vygenerovanou hodnotu hash.  
  
 `cchHash`  
 pro Maximální velikost vyrovnávací paměti, na kterou `pbHash` odkazuje.  
  
 `pchHash`  
 mimo Velikost vracené `pbHash`velikosti (v bajtech)  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je stejná jako [GetHashFromFileW –](gethashfromfilew-function.md)s tím rozdílem, že specifikace názvu souboru je ANSI namísto Unicode.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** StrongName. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetHashFromFile – metoda](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW – metoda](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

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
ms.openlocfilehash: ea2b70f37668587fb02513ab54da6c1915e2918d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176978"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile – funkce
Generuje hash nad obsahem zadaného souboru.  
  
 Tato funkce byla zastaralá. Místo toho použijte metodu [ICLRStrongName::GetHashFromFile.](../hosting/iclrstrongname-gethashfromfile-method.md)  
  
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
 [v] Název souboru hash.  
  
 `piHashAlg`  
 [dovnitř, ven] Algoritmus, který se má použít při generování algoritmu hash. Platné algoritmy jsou ty, které jsou definovány Win32 CryptoAPI. Pokud `piHashAlg` je nastavena na hodnotu 0, použije se výchozí algoritmus CALG_SHA-1.  
  
 `pbHash`  
 [out] Bajtový pole obsahující vygenerovaný hash.  
  
 `cchHash`  
 [v] Maximální velikost vyrovnávací paměti, která `pbHash` odkazuje na.  
  
 `pchHash`  
 [out] Velikost vráceného bajtu v bajtech `pbHash`.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je stejná jako [GetHashFromFileW](gethashfromfilew-function.md), s tím rozdílem, že specifikace názvu souboru je ANSI místo Unicode.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetHashFromFile – metoda](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW – metoda](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

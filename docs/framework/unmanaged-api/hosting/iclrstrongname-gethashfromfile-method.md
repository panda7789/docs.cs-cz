---
title: ICLRStrongName::GetHashFromFile – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: ed735c3d7830551581df35793f3f6fdc4953dc8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178077"
---
# <a name="iclrstrongnamegethashfromfile-method"></a>ICLRStrongName::GetHashFromFile – metoda
Generuje hash nad obsahem zadaného souboru.  
  
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
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`pokud byla metoda úspěšně dokončena; jinak hodnota HRESULT, která označuje selhání (viz [běžné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je stejná jako metoda [ICLRStrongName::GetHashFromFileW,](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) s tím rozdílem, že specifikace názvu souboru je ANSI místo Unicode.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetHashFromFileW – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

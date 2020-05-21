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
ms.openlocfilehash: e4a5f6440a016176cf06704b342c173b29748e78
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762107"
---
# <a name="iclrstrongnamegethashfromfile-method"></a>ICLRStrongName::GetHashFromFile – metoda
Vygeneruje hodnotu hash přes obsah zadaného souboru.  
  
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
 [in, out] Algoritmus, který má být použit při generování hodnoty hash. Platné algoritmy jsou definovány rozhraním Win32 CryptoAPI. Pokud `piHashAlg` je nastavena na hodnotu 0, je použit výchozí algoritmus CALG_SHA-1.  
  
 `pbHash`  
 mimo Bajtové pole obsahující vygenerovanou hodnotu hash.  
  
 `cchHash`  
 pro Maximální velikost vyrovnávací paměti, na kterou `pbHash` odkazuje.  
  
 `pchHash`  
 mimo Velikost vracené velikosti (v bajtech) `pbHash`  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je stejná jako metoda [ICLRStrongName:: GetHashFromFileW –](iclrstrongname-gethashfromfilew-method.md) s tím rozdílem, že specifikace názvu souboru je ANSI namísto Unicode.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetHashFromFileW – metoda](iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)

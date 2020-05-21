---
title: ICLRStrongName::GetHashFromFileW – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
ms.openlocfilehash: 6dbb3360132186c38c007fb5fa12a3724ca145aa
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762094"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a>ICLRStrongName::GetHashFromFileW – metoda
Vygeneruje hodnotu hash přes obsah souboru určeného řetězcem Unicode.  
  
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
 [in, out] Algoritmus, který má být použit při generování hodnoty hash. Platné algoritmy jsou definovány rozhraním Win32 CryptoAPI. Pokud `piHashAlg` je nastavena na hodnotu 0, je použit výchozí algoritmus CALG_SHA-1.  
  
 `pbHash`  
 mimo Bajtové pole obsahující vygenerovanou hodnotu hash.  
  
 `cchHash`  
 pro Maximální velikost vyrovnávací paměti, na kterou ukazuje `pbHash` .  
  
 `pchHash`  
 mimo Velikost v bajtech `pbHash` .  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je stejná jako metoda [ICLRStrongName:: GetHashFromFile –](iclrstrongname-gethashfromfile-method.md) s tím rozdílem, že specifikace názvu souboru je Unicode namísto ANSI.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetHashFromFile – metoda](iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)

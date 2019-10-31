---
title: ICLRStrongName::GetHashFromAssemblyFileW – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
ms.openlocfilehash: 43a5cd57a8eeaba70f1bb1ffb9cab5bb1a067914
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130955"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a>ICLRStrongName::GetHashFromAssemblyFileW – metoda
Vygeneruje hodnotu hash přes obsah souboru určeného řetězcem Unicode.  
  
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
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetHashFromAssemblyFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

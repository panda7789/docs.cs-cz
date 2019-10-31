---
title: ICLRStrongName::GetHashFromHandle – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
ms.openlocfilehash: 19d4518b7ec125df717b2f901bbd92cbd1b659bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135168"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a>ICLRStrongName::GetHashFromHandle – metoda
Vygeneruje hodnotu hash přes obsah souboru, který má zadaný popisovač souboru, pomocí zadaného algoritmu hash.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hFile`  
 pro Popisovač souboru, který se má vyhodnotit.  
  
 `piHashAlg`  
 [in, out] Konstanta, která určuje algoritmus hash. Pro výchozí algoritmus použijte nulu.  
  
 `pbHash`  
 mimo Vrácená vyrovnávací paměť hash.  
  
 `cchHash`  
 pro Požadovaná maximální velikost `pbHash`.  
  
 `pchHash`  
 mimo Velikost vrácených `pbHash`v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

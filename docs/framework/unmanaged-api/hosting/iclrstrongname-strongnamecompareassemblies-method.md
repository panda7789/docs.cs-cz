---
title: ICLRStrongName::StrongNameCompareAssemblies – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: fdca03b781e07b709cbc54e673dbaa2a1130fbe3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135151"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a>ICLRStrongName::StrongNameCompareAssemblies – metoda
Určuje, zda se dvě sestavení liší pouze signaturami silného názvu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAssembly1`  
 pro Cesta k prvnímu sestavení  
  
 `wszAssembly2`  
 pro Cesta k druhému sestavení  
  
 `pdwResult`  
 mimo Jedna z následujících hodnot:  
  
- `SN_CMP_DIFFERENT` (0) – určuje, že sestavení obsahují odlišná data.  
  
- `SN_CMP_IDENTICAL` (1) – určuje, že sestavení jsou přesně stejná, včetně jejich podpisů a kontrolního součtu.  
  
- `SN_CMP_SIGONLY` (2) – určuje, že se sestavení liší pouze pomocí signatury a kontrolního součtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a>Poznámky  
 Podpis silného názvu sestavení se skládá z textového názvu sestavení, verze, jazykové verze a tokenu veřejného klíče.  
  
## <a name="see-also"></a>Viz také:

- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

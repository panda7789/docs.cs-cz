---
title: ICLRStrongName::StrongNameFreeBuffer – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
ms.openlocfilehash: 7aed3e6877bfcd83754d462cdba81ccc229d002f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504001"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a>ICLRStrongName::StrongNameFreeBuffer – metoda
Uvolní paměť, která byla přidělena předchozímu volání metody silného názvu, jako je například [ICLRStrongName:: StrongNameGetPublicKey –](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName:: StrongNameTokenFromPublicKey –](iclrstrongname-strongnametokenfrompublickey-method.md)nebo [ICLRStrongName:: StrongNameSignatureGeneration –](iclrstrongname-strongnamesignaturegeneration-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbMemory`  
 pro Ukazatel na paměť, která má být uvolněna.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)

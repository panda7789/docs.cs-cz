---
title: ICLRStrongName::StrongNameSignatureVerificationEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da9b0fd4fd7c7eadf09f0b76a17e60b1840fdf48
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404907"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a>ICLRStrongName::StrongNameSignatureVerificationEx – metoda
Získá hodnotu, která určuje, zda obsahuje manifest sestavení v zadané cestě podpis silného názvu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Cesta k přenositelný spustitelný soubor (.exe nebo .dll) soubor pro sestavení, který se má ověřit.  
  
 `fForceVerification`  
 [in] `true` provádět ověřování, i když je potřeba přepsat nastavení registru; v opačném případě `false`.  
  
 `pfWasVerified`  
 [out] `true` Pokud byl podpis silného názvu ověřené; v opačném případě `false`. `pfWasVerified` je také nastavena na `false` Pokud bude ověření úspěšné z důvodu nastavení registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud bude ověření úspěšné; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).  
  
## <a name="remarks"></a>Poznámky  
 [Iclrstrongname::strongnamesignatureverificationex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metoda poskytuje podobné funkce [iclrstrongname::strongnamesignatureverification –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) metody. Ale druhé vstupní parametr a výstupní parametr pro [iclrstrongname::strongnamesignatureverificationex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) jsou typu `BOOLEAN` místo `DWORD`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameSignatureVerification – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

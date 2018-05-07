---
title: StrongNameSignatureVerificationEx2 – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d2ac3788b68626eb04a6f2cbac995b8e5b4ebf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="strongnamesignatureverificationex2-method"></a>StrongNameSignatureVerificationEx2 – metoda
Ověří podpis silně pojmenované sestavení a poskytuje mapování z klíče ECMA skutečné klíče.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [v] Cesta k přenosné spustitelný soubor (.exe nebo .dll) souboru pro sestavení, které má být ověřen.  
  
 `fForceVerification`  
 [v] `true` provést ověření, i když je nezbytné pro přepsání nastavení registru; v opačném `false`.  
  
 `pbEcmaPublicKey`  
 [v] Ukazatel na mapování z ECMA veřejný klíč do skutečné klíče používané pro ověřování.  
  
 `cbEcmaPublicKey`  
 [v] Délka skutečné ECMA veřejný klíč.  
  
 `pfWasVerified`  
 [out] `true` Pokud podpis silného názvu byl ověřený, jinak hodnota `false`. Tento parametr je také nastavena na `false` Pokud ověření bylo úspěšné z důvodu nastavení registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud ověření byla úspěšná. jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameSignatureVerification – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [StrongNameSignatureVerificationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

---
title: ICLRStrongName::StrongNameKeyGen – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55b4fbb8785f788c9eb34f32b5078201f8253066
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a>ICLRStrongName::StrongNameKeyGen – metoda
Vytvoří nový pár veřejného a privátního klíče pro silné jméno použití.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszKeyContainer`  
 [v] Název požadovaný kontejner klíčů. `wszKeyContainer` musí být neprázdný řetězec nebo hodnota null pro generování dočasný název.  
  
 `dwFlags`  
 [v] Hodnota, která určuje, zda chcete ponechat klíč zaregistrován. Podporovány jsou následující hodnoty:  
  
-   0x00000000 - použít, když `wszKeyContainer` má hodnotu null při generování názvu dočasné kontejneru klíčů.  
  
-   0x00000001 (`SN_LEAVE_KEY`)-určuje, které by měl být klíč vlevo registrován.  
  
 `ppbKeyBlob`  
 [out] Vrácený veřejného a privátního klíče RSA.  
  
 `pcbKeyBlob`  
 [out] Velikost v bajtech z `ppbKeyBlob`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).  
  
## <a name="remarks"></a>Poznámky  
 [Iclrstrongname::strongnamekeygen –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metoda vytvoří klíč 1024 bitů. Po načtení klíč by měly volat [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodu pro uvolnění přidělenou paměť.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameKeyGenEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

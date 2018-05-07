---
title: StrongNameTokenFromAssemblyEx – funkce
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20bafd0dfc455538292e47ca33508c251ad68614
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="strongnametokenfromassemblyex-function"></a>StrongNameTokenFromAssemblyEx – funkce
Vytvoří token silným názvem ze zadaného souboru sestavení a vrátí veřejný klíč, který představuje daný token.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnametokenfromassemblyex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [v] Cesta k souboru přenosné spustitelný soubor (PE) pro sestavení.  
  
 `ppbStrongNameToken`  
 [out] Token vrácený silným názvem.  
  
 `pcbStrongNameToken`  
 [out] Velikost v bajtech, silný název tokenu.  
  
 `ppbPublicKeyBlob`  
 [out] Vrácený veřejný klíč.  
  
 `pcbPublicKeyBlob`  
 [out] Velikost v bajtech, veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Při úspěšném dokončení; v opačném `false`.  
  
## <a name="remarks"></a>Poznámky  
 Zkrácený tvar veřejný klíč je token silným názvem. Token je 64 bitů hodnotu hash, který je vytvořený z veřejný klíč používaný k podepisování sestavení. Token je součástí silného názvu pro sestavení a můžete číst z metadata sestavení.  
  
 Jakmile načítání klíče a token je vytvořen, by měly volat [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce k uvolnění přidělenou paměť.  
  
 Pokud `StrongNameTokenFromAssemblyEx` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** zahrnuty jako prostředek v mscoree.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameTokenFromAssemblyEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [StrongNameTokenFromAssembly – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

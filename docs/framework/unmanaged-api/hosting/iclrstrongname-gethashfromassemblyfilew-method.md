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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36e4f07f04968579be2e42efad666b0453cc4796
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a>ICLRStrongName::GetHashFromAssemblyFileW – metoda
Generuje součet hash přes obsah soubor určený touto řetězec znaků Unicode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [v] Cesta k souboru, který se použít algoritmus hash. Tento parametr musí být řetězec znaků Unicode.  
  
 `piHashAlg`  
 [ve out] Konstanta, která určuje algoritmus hash. Používejte nula pro výchozí algoritmus hash.  
  
 `pbHash`  
 [out] Vrácená hodnota hash vyrovnávací paměti.  
  
 `cchHash`  
 [v] Požadovaný maximální velikost `pbHash`.  
  
 `pchHash`  
 [out] Vrácen velikost v bajtech, z `pbHash`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [GetHashFromAssemblyFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

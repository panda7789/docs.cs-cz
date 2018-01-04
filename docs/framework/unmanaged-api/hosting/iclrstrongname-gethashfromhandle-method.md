---
title: "ICLRStrongName::GetHashFromHandle – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61e0f0cc5ba4bb48f5d54427f6e94f72ef8fbd00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromhandle-method"></a>ICLRStrongName::GetHashFromHandle – metoda
Generuje součet hash přes obsah souboru, který má zadaný soubor popisovač, pomocí zadaný algoritmus hash.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hFile`  
 [v] Popisovač souboru, který se použít algoritmus hash.  
  
 `piHashAlg`  
 [ve out] Konstanta, která určuje algoritmus hash. Používejte nula pro výchozí algoritmus.  
  
 `pbHash`  
 [out] Vrácená hodnota hash vyrovnávací paměti.  
  
 `cchHash`  
 [v] Požadovaný maximální velikost `pbHash`.  
  
 `pchHash`  
 [out] Velikost v bajtech vrácený `pbHash`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

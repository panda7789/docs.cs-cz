---
title: "ICLRStrongName::StrongNameSignatureSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureSize
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a961cca6bba24ac8a2428a20c616a2ee074b8abf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a>ICLRStrongName::StrongNameSignatureSize – metoda
Vrátí velikost podpis silného názvu. Tato metoda se obvykle používá kompilátory, chcete-li zjistit, kolik místa vyhradit v souboru při vytváření sestavení se zpožděním podepsané.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 [v] Struktura typu [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů sloužící ke generování podpis silného názvu.  
  
 `cbPublicKeyBlob`  
 [v] Velikost v bajtech z `pbPublicKeyBlob`.  
  
 `pcbSize`  
 [v] Počet bajtů požadovaných k uložení podpis silného názvu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

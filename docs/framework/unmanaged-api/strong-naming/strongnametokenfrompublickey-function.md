---
title: "StrongNameTokenFromPublicKey – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: COM
f1_keywords: StrongNameTokenFromPublicKey
helpviewer_keywords: StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0cb649f43bfea2e11c986aa3fff5a702e2b58c25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey – funkce
Získá token představující veřejný klíč. Zkrácený tvar veřejný klíč je token silným názvem.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 [v] Struktura typu [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů sloužící ke generování podpis silného názvu.  
  
 `cbPublicKeyBlob`  
 [v] Velikost v bajtech z `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 [out] Silný název tokenu odpovídající klíč předaná `pbPublicKeyBlob`. Modul common language runtime přidělí paměť k vrácení tokenu. Volající musí uvolněte tuto paměť pomocí [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce.  
  
 `pcbStrongNameToken`  
 [out] Velikost v bajtech, vrácený silný název tokenu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Při úspěšném dokončení; v opačném `false`.  
  
## <a name="remarks"></a>Poznámky  
 Silný název tokenu je zkrácený tvar veřejný klíč používaný ušetřit místo na při ukládání informací o klíči v metadatech. Konkrétně silným názvem tokeny se používají v odkazy na sestavení odkazovat na závislého sestavení.  
  
 Pokud `StrongNameTokenFromPublicKey` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** zahrnuty jako prostředek v mscoree.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameTokenFromPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [StrongNameGetPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [PublicKeyBlob – struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)

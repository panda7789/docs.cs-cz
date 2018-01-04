---
title: "StrongNameGetBlobFromImage – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlobFromImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlobFromImage
helpviewer_keywords: StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3dd5fa1838517baa97079f5d7f75a789384255a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamegetblobfromimage-function"></a>StrongNameGetBlobFromImage – funkce
Získá binární reprezentace sestavení image na adrese zadaná paměťová.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnamegetblobfromimage –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbBase`  
 [v] Adresa paměti manifest namapované sestavení.  
  
 `dwLength`  
 [v] Velikost v bajtech bitové kopie `pbBase`.  
  
 `pbBlob`  
 [v] Vyrovnávací paměť pro obsahovat binární reprezentace bitovou kopii.  
  
 `pcbBlob`  
 [ve out] Požadovanou maximální velikost v bajtech `pbBlob`. Po návratu, skutečná velikost v bajtech z `pbBlob`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Při úspěšném dokončení; v opačném `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `StrongNameGetBlobFromImage` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameGetBlobFromImage – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [StrongNameGetBlob – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

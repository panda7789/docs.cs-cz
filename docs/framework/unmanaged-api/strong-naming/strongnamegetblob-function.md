---
title: "StrongNameGetBlob – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlob
helpviewer_keywords: StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1948a0d8a8536ebe9b0531eecaf3df446252b0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob – funkce
Vyplní zadanou vyrovnávací paměť binární reprezentace spustitelný soubor na zadané adrese.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnamegetblob –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [v] Platná cesta ke spustitelnému souboru, který má být načten.  
  
 `pbBlob`  
 [v] Vyrovnávací paměť, do kterého se načíst spustitelný soubor.  
  
 `pcbBlob`  
 [ve out] Požadovanou maximální velikost v bajtech `pbBlob`. Po návratu, skutečná velikost v bajtech z `pbBlob`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Při úspěšném dokončení; v opačném `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `StrongNameGetBlob` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameGetBlob – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [StrongNameGetBlobFromImage – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

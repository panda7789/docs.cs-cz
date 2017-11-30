---
title: "ICorPublishAppDomain::GetName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomain.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9807f914c767cc212bf97d83042e76d42a3d9440
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName – metoda
Získá název domény aplikace, která je reprezentována to [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchName`  
 [v] Velikost `szName` pole.  
  
 `pcchName`  
 [out] Ukazatel na počet široké znaky, včetně znak hodnoty null, vrátí se v `szName` pole.  
  
 `szName`  
 [out] Pole, do které chcete uložit název.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `szName` hodnotu Null, `GetName` metoda zkopíruje až `cchName` znaků (včetně null ukončovací znak) do `szName`. Pokud se vrátí hodnotu null v `pcchName`, skutečný počet znaků v názvu (včetně null ukončovací znak) je uložen v `szName` pole.  
  
 `GetName` Metoda vrátí HRESULT S_OK bez ohledu na to, kolik znaků byly zkopírovány.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorPublishAppDomain – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)

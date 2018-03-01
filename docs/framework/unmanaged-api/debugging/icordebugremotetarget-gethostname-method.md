---
title: "ICorDebugRemoteTarget::GetHostName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45fa4afebda00cb2549a5c18ba81c6bb4e8210e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName – metoda
Vrátí plně kvalifikovaný název domény nebo adresu IPv4 vzdáleného ladění cílového počítače. Protokol IPV6 není podporován v tuto chvíli.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchHostName`  
 [v] Velikost v znaků, z `szHostName` vyrovnávací paměti. Pokud má parametr hodnotu 0 (nula), `szHostName` musí mít hodnotu null.  
  
 `pcchHostName`  
 [out] Počet znaků, včetně zakončením null v názvu hostitele nebo IP adresu. Tento parametr může mít hodnotu null.  
  
 `szHostName`  
 [out] Vyrovnávací paměť, která obsahuje název hostitele nebo IP adresu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Název hostitele nebo IP adresa byla úspěšně vrácena.  
  
 E_FAIL (nebo ostatní návratové kódy E_)  
 Nelze vrátit název hostitele nebo IP adresu.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je implementována zapisovačem ladicí program. Musí mít více zlepší volání: při prvním volání volající předá hodnotu null na obě `cchHostName` a `szHostName`, a `pcchHostName` vrátí velikost požadované vyrovnávací paměti. Na druhé volání, je předaná velikost, která byla předtím vrátila `cchHostName`, a je správně velikosti vyrovnávací paměti předaná `szHostName`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 3.5 SP1  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugRemoteTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

---
title: ICorDebugAppDomain::IsAttached – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0412089fee27e556c2f9230e9b34de3391b9bd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomainisattached-method"></a>ICorDebugAppDomain::IsAttached – metoda
Získá hodnotu, která určuje, zda je ladicí program připojen do domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbAttached`  
 [out] `true` Pokud ladicího programu je připojené k doméně aplikace, jinak hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 ICorDebugController metody nemohou používat, dokud ladicí program připojí k doméně aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

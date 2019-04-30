---
title: ICorDebugAppDomain::GetObject – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ca9792df69f859e20f1d9e40754d1cec138945d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785109"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject – metoda
Získá ukazatel rozhraní common language runtime (CLR) aplikační doménu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppObject`  
 [out] Ukazatel na adresu objektu rozhraní ICorDebugValue, který představuje doménu aplikace modulu CLR.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud spravované <xref:System.AppDomain?displayProperty=nameWithType> objekt nebyl byl vytvořen pro tuto doménu aplikace, vrátí metoda `S_FALSE` a umístí `NULL` v `*ppObject`.  
  
## <a name="remarks"></a>Poznámky  
 Každá doména aplikace v procesu může mít spravované <xref:System.AppDomain?displayProperty=nameWithType> objektu v modulu runtime, který ho zastupuje. Tato funkce získá icordebugvalue – rozhraní objekt, který odpovídá této spravované <xref:System.AppDomain?displayProperty=nameWithType> objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

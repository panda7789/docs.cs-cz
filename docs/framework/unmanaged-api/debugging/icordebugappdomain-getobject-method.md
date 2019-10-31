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
ms.openlocfilehash: f2c881603cfa0e4b3d2dc8d1e996631b51d1e850
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134703"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject – metoda
Načte ukazatel rozhraní do aplikační domény modulu CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppObject`  
 mimo Ukazatel na adresu objektu rozhraní ICorDebugValue, který představuje doménu aplikace CLR.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud objekt spravovaného <xref:System.AppDomain?displayProperty=nameWithType> nebyl vytvořen pro tuto doménu aplikace, metoda vrátí `S_FALSE` a umístí `NULL` do `*ppObject`.  
  
## <a name="remarks"></a>Poznámky  
 Každá doména aplikace v procesu může mít spravovaný objekt <xref:System.AppDomain?displayProperty=nameWithType> v modulu runtime, který ho představuje. Tato funkce získá objekt rozhraní ICorDebugValue, který odpovídá tomuto spravovanému objektu <xref:System.AppDomain?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

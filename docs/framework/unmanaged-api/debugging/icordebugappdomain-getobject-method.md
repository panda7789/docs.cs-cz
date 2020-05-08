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
ms.openlocfilehash: a21f3b36e418bbde5dcb90f25a39dae03fde77c9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895213"
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
 Pokud nebyl pro <xref:System.AppDomain?displayProperty=nameWithType> tuto doménu aplikace vytvořen spravovaný objekt, metoda vrátí `S_FALSE` a umístí do `NULL` `*ppObject`umístění.  
  
## <a name="remarks"></a>Poznámky  
 Každá doména aplikace v procesu může mít spravovaný <xref:System.AppDomain?displayProperty=nameWithType> objekt v modulu runtime, který ho představuje. Tato funkce získá objekt rozhraní ICorDebugValue, který odpovídá tomuto spravovanému <xref:System.AppDomain?displayProperty=nameWithType> objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

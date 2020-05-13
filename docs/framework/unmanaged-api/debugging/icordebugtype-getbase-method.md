---
title: ICorDebugType::GetBase – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
ms.openlocfilehash: fc406f6e87e5b2be48c6fe7d5fc988774ac5cd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379988"
---
# <a name="icordebugtypegetbase-method"></a>ICorDebugType::GetBase – metoda
Získá ukazatel rozhraní na ICorDebugType, který představuje základní typ, pokud existuje, typu reprezentovaného tímto `ICorDebugType` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pBase`  
 mimo Ukazatel na adresu `ICorDebugType` objektu, který představuje základní typ.  
  
## <a name="remarks"></a>Poznámky  
 Vyhledávání základního typu pro typ je užitečné pro implementaci běžných funkcí ladicího programu, jako je například tisk všech polí objektu nebo jeho nadřazených tříd.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

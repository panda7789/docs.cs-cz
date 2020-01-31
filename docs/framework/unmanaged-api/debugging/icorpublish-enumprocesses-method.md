---
title: ICorPublish::EnumProcesses – metoda
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 5f785b22a3fbda6403c124ec70757b16f5335907
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790757"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses – metoda
Získá enumerátor pro spravované procesy, které jsou spuštěny na tomto počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Type`  
 Hodnota výčtu [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) , která určuje typ procesu, který se má načíst. V aktuální verzi je platná pouze COR_PUB_MANAGEDONLY.  
  
 `ppIEnum`  
 Ukazatel na adresu instance [ICorPublishProcessEnum –](icorpublishprocessenum-interface.md) , která je enumerátorem procesů.  
  
## <a name="remarks"></a>Poznámky  
 Kolekce procesů výčtu je založena na snímku procesů, které jsou spuštěny při volání metody `EnumProcesses`. Enumerátor nebude zahrnovat žádné procesy, které se ukončí nebo spustí po volání `EnumProcesses`.  
  
 Metodu `EnumProcesses` lze v této instanci [ICorPublish –](icorpublish-interface.md) volat více než jednou, aby bylo možné vytvořit novou aktuální kolekci procesů. Existující kolekce nebudou ovlivněny následnými voláními metody `EnumProcesses`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorPublish – rozhraní](icorpublish-interface.md)

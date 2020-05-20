---
title: ICorPublishProcess::IsManaged – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 3eec84624866b2be7068d7875cd650828c283fd2
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421095"
---
# <a name="icorpublishprocessismanaged-method"></a>ICorPublishProcess::IsManaged – metoda
Získá hodnotu, která označuje, zda se má proces, na který odkazuje tento [ICorPublishProcess](icorpublishprocess-interface.md) , známo, že má spravovaný kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbManaged`  
 mimo Ukazatel na logickou hodnotu, která určuje, zda má proces spravovaný kód. Hodnota je v `true` případě, že proces má spravovaný kód. v opačném případě `false` .  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že aktuální verze nástroje `ICorPublishProcess` umožňuje přístup pouze k procesům, které mají spravovaný kód, `IsManaged` vždy vrátí `true` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorPublishProcess – rozhraní](icorpublishprocess-interface.md)

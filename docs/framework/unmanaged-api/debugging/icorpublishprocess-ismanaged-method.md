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
ms.openlocfilehash: 68931ba16ea1f8f61176c6d6ed8300e762b61690
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790528"
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
 mimo Ukazatel na logickou hodnotu, která určuje, zda má proces spravovaný kód. Hodnota je `true`, pokud má proces spravovaný kód. v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že aktuální verze `ICorPublishProcess` umožňuje přístup pouze k procesům se spravovaným kódem, `IsManaged` vždy vrací `true`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorPublishProcess – rozhraní](icorpublishprocess-interface.md)

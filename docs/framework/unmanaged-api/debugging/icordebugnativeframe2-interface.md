---
title: ICorDebugNativeFrame2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
ms.openlocfilehash: cd2a2821128ad9265e8a831f7b02792e6453b1ee
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213787"
---
# <a name="icordebugnativeframe2-interface"></a>ICorDebugNativeFrame2 – rozhraní
Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IsChild – metoda](icordebugnativeframe2-ischild-method.md)|Určuje, zda je aktuální rámec podřízeným rámcem.|  
|[IsMatchingParentFrame – metoda](icordebugnativeframe2-ismatchingparentframe-method.md)|Určuje, zda je určený rámec nadřazeným prvkem aktuálního rámce.|  
|[GetStackParameterSize – metoda](icordebugnativeframe2-getstackparametersize-method.md)|Vrátí kumulativní velikost parametrů v zásobníku v operačních systémech x86.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní logicky rozšiřuje rozhraní "ICorDebugNativeFrame".  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)

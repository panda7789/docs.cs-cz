---
title: "ICorDebugILFrame2::RemapFunction – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2.RemapFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9fed4759576d1b6d2fec1a5e9c1e36019e5944c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction – metoda
Znovu mapuje upravená funkce zadáním nového posun (MSIL intermediate language) společnosti Microsoft  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `newILOffset`  
 [v] Rámec zásobníku nové MSIL odsazení, kdy má být umístěn ukazatel instrukce Tato hodnota musí být bodu sekvence.  
  
 Je odpovědností volajícího zajistit platnost této hodnoty. Posun MSIL například není platný, pokud je mimo rozsah funkce.  
  
## <a name="remarks"></a>Poznámky  
 Pokud bylo upraveno funkce rámečku, můžete volat ladicí program `RemapFunction` metoda do odkládacího souboru v nejnovější verzi funkce rámečku, mohou být provedeny. Provádění kódu zahájíte na danou MSIL posunu.  
  
> [!NOTE]
>  Volání metody `RemapFunction`, například volání [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), hned zruší platnost všech ladění rozhraní, které se vztahují k generování trasování zásobníku pro vlákno. Tato rozhraní zahrnují [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, icordebuginternalframe – a ICorDebugNativeFrame.  
  
 `RemapFunction` Metodu lze volat pouze v kontextu aktuálního snímku a pouze v jednom z následujících případech:  
  
-   Po přijetí [icordebugmanagedcallback2::functionremapopportunity –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) zpětné volání, které nebyl ještě dál.  
  
-   Při provádění kódu je zastavena z důvodu [icordebugmanagedcallback::editandcontinueremap –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) události pro tento snímek.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

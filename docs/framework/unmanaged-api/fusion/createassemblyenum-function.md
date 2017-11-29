---
title: "CreateAssemblyEnum – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyEnum
helpviewer_keywords: CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c229496a79b146b5dcac3d06fa3efd9237e39d3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum – funkce
Získá odkazy [iassemblyenum –](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instanci, která můžete vytvořit výčet objektů v sestavení se zadaným [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pEnum`  
 [out] Ukazatel na umístění paměti, která obsahuje požadovanou `IAssemblyEnum` ukazatel.  
  
 `pUnkReserved`  
 [v] Vyhrazeno pro budoucí rozšíření. `pUnkReserved`musí být odkaz s hodnotou null.  
  
 `pName`  
 [v] `IAssemblyName` Požadovaný sestavení. Tento název se používá k filtrování výčtu. Může být null výčet všechna sestavení v globální mezipaměti sestavení.  
  
 `dwFlags`  
 [v] Příznaky úpravy chování enumerátor. Tento parametr obsahuje přesně jeden bit z [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) výčtu.  
  
 `pvReserved`  
 [v] Vyhrazeno pro budoucí rozšíření. `pvReserved`musí být odkaz s hodnotou null.  
  
## <a name="remarks"></a>Poznámky  
 `dwFlags` Parametr obsahuje přesně jeden bit z `ASM_CACHE_FLAGS` výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Iassemblyenum – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [Iassemblyname – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [Fúze globálních statických funkcí](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

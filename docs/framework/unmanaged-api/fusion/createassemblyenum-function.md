---
title: CreateAssemblyEnum – funkce
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1db72c44b53b5abff9aee35094abc1e0e577fad4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795386"
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum – funkce
Získá ukazatel na instanci [IAssemblyEnum](iassemblyenum-interface.md) , která může vytvořit výčet objektů v sestavení pomocí zadaného [IAssemblyName](iassemblyname-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `pEnum`  
 mimo Ukazatel na umístění v paměti, které obsahuje požadovaný `IAssemblyEnum` ukazatel.  
  
 `pUnkReserved`  
 pro Vyhrazeno pro budoucí rozšíření. `pUnkReserved`musí se jednat o odkaz s hodnotou null.  
  
 `pName`  
 pro `IAssemblyName` Z požadovaného sestavení. Tento název slouží k filtrování výčtu. Aby bylo možné vytvořit výčet všech sestavení v globální mezipaměti sestavení (GAC), může mít hodnotu null.  
  
 `dwFlags`  
 pro Příznaky pro úpravu chování čítače výčtu. Tento parametr obsahuje přesně jeden bit z výčtu [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) .  
  
 `pvReserved`  
 pro Vyhrazeno pro budoucí rozšíření. `pvReserved`musí se jednat o odkaz s hodnotou null.  
  
## <a name="remarks"></a>Poznámky  
 Parametr obsahuje přesně jeden bit `ASM_CACHE_FLAGS` z výčtu. `dwFlags`  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Fusion. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IAssemblyEnum – rozhraní](iassemblyenum-interface.md)
- [IAssemblyName – rozhraní](iassemblyname-interface.md)
- [Globální statické funkce pro fúze](fusion-global-static-functions.md)

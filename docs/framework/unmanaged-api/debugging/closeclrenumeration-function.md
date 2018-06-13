---
title: CloseCLREnumeration – funkce
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18903bd00b0a9d09365d03c155531a25dc013189
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406085"
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration – funkce
Zavře všechny platné běžné jazyk runtime (CLR) pokračovat spuštění události umístěné v pole vrácené obslužné rutiny [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)a uvolní paměť pro cestu pole popisovač a řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pHandleArray`  
 [v] Ukazatel na pole obslužných rutin událostí vrácených [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `pStringArray`  
 [v] Ukazatel na pole CLR řetězec cesty vrácená z [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `dwArrayLength`  
 [v] DWORD, který obsahuje velikost (délka) buď `pHandleArray` nebo `pStringArray` (jde o stejný).  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Obslužné rutiny otevřít [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) zavřou, a je paměť přidělená pro pole popisovač a řetězec vydání.  
  
 E_INVALIDARG  
 Délka `pHandleArray` neodpovídá délka, který se předává v `dwArrayLength`.  
  
 E_FAIL (nebo ostatní návratové kódy E_)  
 Funkce nelze uvolnit paměť pro `pHandleArray` a `pStringArray`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim.h  
  
 **Knihovna:** dbgshim.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1

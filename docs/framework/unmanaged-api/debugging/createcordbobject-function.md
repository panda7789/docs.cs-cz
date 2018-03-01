---
title: "CreateCordbObject – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7007e541e9999e0cb14a83845eb28d71336b3ff6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="createcordbobject-function"></a>CreateCordbObject – funkce
Vytvoří rozhraní ladicího programu ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)), poskytuje funkce pro vytváření instancí spravované ladicí relace na vzdálený proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iDebuggerVersion`  
 [v] Ladicí program verze tento cílový proces. Tento parametr musí být CorDebugVersion_2_0 pro vzdálené ladění.  
  
 `ppCordb`  
 [out] Ukazatel na ukazatel na objekt, který bude přetypovat [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní a vrácena.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Počet CLRs v procesu byla úspěšně zjistit a byly správně zadat odpovídající popisovač a cesta pole.  
  
 E_INVALIDARG  
 `ppCordb`má hodnotu null, nebo `iDebuggerVersion` není CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Nelze přidělit dostatek paměti pro`ppCordb`  
  
 E_FAIL (nebo ostatní návratové kódy E_)  
 Jiné chyby.  
  
## <a name="remarks"></a>Poznámky  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní, které je vrácený v `ppCordb` je nejvyšší úrovně ladění rozhraní pro všechny spravované ladění služeb.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Knihovna:** mscordbi_macx86.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1

---
title: "IBindingDisplay::GetCurrentDisplay – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IBindingDisplay.GetCurrentDisplay
api_location: diasymreader.dll
api_type: COM
f1_keywords: IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7013b07d0ebf2709d6c2b6f791960a8e7d35d678
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a>IBindingDisplay::GetCurrentDisplay – metoda
Vrátí informace o zobrazení aktuální vazby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `display`  
 [out, retval] Ukazatel na safearray obsahující informace o vazbě zobrazení.  
  
## <a name="remarks"></a>Poznámky  
 [Ibindingdisplay::initializeforprocess –](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) metoda musí mít dříve bylo úspěšně dokončeno a program musí být zastavena ladicí program.  
  
 Volající musí navrácení vrácený `SAFEARRAY` paměti pomocí [SafeArrayDestroy](http://msdn.microsoft.com/en-us/fc94f7e7-b903-4c78-905c-54df1f8d13fa).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** BindingDisplay.h  
  
 **Knihovna:** BindingDisplay.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IBindingDisplay – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 [InitializeForProcess – metoda](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)

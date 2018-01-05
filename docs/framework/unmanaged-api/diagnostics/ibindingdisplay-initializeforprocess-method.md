---
title: "IBindingDisplay::InitializeForProcess – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IBindingDisplay.InitializeForProcess
api_location: diasymreader.dll
api_type: COM
f1_keywords: IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56f55788fcaf08507f413a03c5364ce3bcdbbf3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>IBindingDisplay::InitializeForProcess – metoda
Inicializuje [ibindingdisplay –](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pid`  
 [v] Identifikátor procesu.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program volání `InitializeForProcess` metoda v okamžiku vytvoření k chybě při inicializaci zobrazení vazby. `InitializeForProcess`musí být volána v okamžiku vytvoření před jinou metodu na `IBindingDisplay` je volána.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** BindingDisplay.h  
  
 **Knihovna:** BindingDisplay.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IBindingDisplay – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)

---
title: IBindingDisplay::InitializeForProcess – metoda
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: 8645878132359b6218cd62b1ff707208de53704b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442147"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>IBindingDisplay::InitializeForProcess – metoda
Inicializuje objekt [IBindingDisplay](ibindingdisplay-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pid`  
 pro Identifikátor procesu.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program volá `InitializeForProcess` metodu v okamžiku vytvoření pro inicializaci zobrazení vazby. `InitializeForProcess`musí být voláno v době vytváření před voláním jakékoli jiné metody `IBindingDisplay` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** BindingDisplay. h  
  
 **Knihovna:** BindingDisplay. idl  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IBindingDisplay – rozhraní](ibindingdisplay-interface.md)

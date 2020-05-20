---
title: IBindingDisplay::GetCurrentDisplay – metoda
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
ms.openlocfilehash: 6fe8c3266a8c9a52cd1022589cd68485c4326fd1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442186"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a>IBindingDisplay::GetCurrentDisplay – metoda
Vrátí aktuální informace o zobrazení vazby.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `display`  
 [out, retval] Ukazatel na pole SAFEARRAY obsahující informace o zobrazení vazby.  
  
## <a name="remarks"></a>Poznámky  
 Metoda [IBindingDisplay:: InitializeForProcess –](ibindingdisplay-initializeforprocess-method.md) musí být dřív úspěšná a program musí být zastavený pomocí ladicího programu.  
  
 Volající musí navrátit vrácenou `SAFEARRAY` paměť pomocí [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** BindingDisplay. h  
  
 **Knihovna:** BindingDisplay. idl  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IBindingDisplay – rozhraní](ibindingdisplay-interface.md)
- [InitializeForProcess – metoda](ibindingdisplay-initializeforprocess-method.md)

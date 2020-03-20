---
title: Funkce CreateIDispatchSTAForwarder – nespravovaný odkaz rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: e151ffa6eb5f1dc7479c699e0d7f9f3f57833ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174716"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>Funkce CreateIDispatchSTAForwarder (WPF Unmanaged API Reference)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno k použití přímo z vašeho kódu.  
  
 Používá infrastrukturu WPF (Windows Presentation Foundation) pro správu vláken a systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a>Parametry  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 pDelegát odeslání  
 Ukazatel na `IDispatch` rozhraní.  
  
 ppForwarder  
 Ukazatel na adresu `IDispatch` rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Požadavky na systém rozhraní .NET Framework](../../get-started/system-requirements.md).  
  
 **Knihovny dll:**  
  
 V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll ll  
  
 V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční informace k nespravovanému rozhraní API WPF](wpf-unmanaged-api-reference.md)

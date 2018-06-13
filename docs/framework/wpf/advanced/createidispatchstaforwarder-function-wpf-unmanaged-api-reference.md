---
title: Funkce CreateIDispatchSTAForwarder (WPF nespravované rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: f7e45d5cafa40ba147fe39888e74a67ac9f95c5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536648"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>Funkce CreateIDispatchSTAForwarder (WPF nespravované rozhraní API)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo z vašeho kódu.  
  
 Používá infrastrukturu Windows Presentation Foundation (WPF) pro přístup z více vláken a windows management.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a>Parametry  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 pDispatchDelegate  
 Ukazatel na `IDispatch` rozhraní.  
  
 ppForwarder  
 Ukazatel na adresu `IDispatch` rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém rozhraní .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **KNIHOVNY DLL:**  
  
 V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll  
  
 V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na nespravované rozhraní API subsystému WPF](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)

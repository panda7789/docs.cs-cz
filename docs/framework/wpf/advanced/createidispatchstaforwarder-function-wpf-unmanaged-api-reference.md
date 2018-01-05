---
title: "Funkce CreateIDispatchSTAForwarder (WPF nespravované rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: CreateIDispatchSTAForwarder
api_location: PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5139784fdc067c09d032c0bf37114e0eb1caac33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na nespravované rozhraní API subsystému WPF](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)

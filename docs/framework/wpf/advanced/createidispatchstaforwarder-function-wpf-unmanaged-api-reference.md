---
title: Funkce CreateIDispatchSTAForwarder – reference nespravovaného rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 67f2542733fb9c6af197c99ede2bd097ce876b5d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738031"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>CreateIDispatchSTAForwarder – funkce (Referenční dokumentace rozhraní API nespravovaného subsystému WPF)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno pro použití přímo v kódu.  
  
 Používáno infrastrukturou Windows Presentation Foundation (WPF) pro vlákna a správu systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a>Parametry  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 pDispatchDelegate  
 Ukazatel na rozhraní `IDispatch`.  
  
 ppForwarder  
 Ukazatel na adresu `IDispatch`ho rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém .NET Framework](../../get-started/system-requirements.md).  
  
 **DLL**  
  
 V .NET Framework 3,0 a 3,5: PresentationHostDLL. dll  
  
 V .NET Framework 4 a novější: PresentationHost_v0400. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Odkaz na nespravované rozhraní API subsystému WPF](wpf-unmanaged-api-reference.md)

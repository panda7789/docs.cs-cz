---
title: Funkce ProcessUnhandledException – reference nespravovaného rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 757e5ac3aa2dc4c87b210b026998523bd82045c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743917"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a>ProcessUnhandledException – funkce (Referenční dokumentace rozhraní API nespravovaného subsystému WPF)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno pro použití přímo v kódu.  
  
 Používá se v infrastruktuře Windows Presentation Foundation (WPF) pro zpracování výjimek.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a>Parametry  
 errorMsg  
 Chybová zpráva  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém .NET Framework](../../get-started/system-requirements.md).  
  
 **DLL**  
  
 V .NET Framework 3,0 a 3,5: PresentationHostDLL. dll  
  
 V .NET Framework 4 a novější: PresentationHost_v0400. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Odkaz na nespravované rozhraní API subsystému WPF](wpf-unmanaged-api-reference.md)

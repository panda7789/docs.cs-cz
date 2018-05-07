---
title: Funkce ProcessUnhandledException (WPF nespravované rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: bcde3fe6d3fdc1749f29a5c9f7625f802dd49535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a>Funkce ProcessUnhandledException (WPF nespravované rozhraní API)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo z vašeho kódu.  
  
 Používá infrastrukturu Windows Presentation Foundation (WPF) pro zpracování výjimek.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 errorMsg  
 Chybová zpráva  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém rozhraní .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **KNIHOVNY DLL:**  
  
 V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll  
  
 V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na nespravované rozhraní API subsystému WPF](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)

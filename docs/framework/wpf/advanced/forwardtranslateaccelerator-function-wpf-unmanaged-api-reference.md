---
title: Funkce ForwardTranslateAccelerator (WPF nespravovaná referenční dokumentace rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: 4bb7e665bb836dc5f95b14f39179f1d4b9f8173d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080251"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>Funkce ForwardTranslateAccelerator (WPF nespravovaná referenční dokumentace rozhraní API)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.  
  
 Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a>Parametry  
 pMsg  
 Ukazatel na zprávu.  
  
 appUnhandled  
 `true` Pokud už je zadaná příležitost dobře se zpracovala zpráva vstupní aplikace, ale nebyla zpracována. v opačném případě `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../get-started/system-requirements.md).  
  
 **DLL:**  
  
 V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll  
  
 V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Odkaz na nespravované rozhraní API subsystému WPF](wpf-unmanaged-api-reference.md)

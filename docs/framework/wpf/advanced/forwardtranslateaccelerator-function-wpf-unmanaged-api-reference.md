---
title: Funkce ForwardTranslateAccelerator – nespravovaný odkaz rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: a0a01be3000dc53df7855cb74015ba1164206838
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186622"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>Funkce ForwardTranslateAccelerator (WPF Unmanaged API Reference)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno k použití přímo z vašeho kódu.  
  
 Používá infrastrukturu WPF (Windows Presentation Foundation) pro správu systému Windows.  
  
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
  
 appNeošetřeno  
 `true`když aplikace již byla dána možnost zpracovat vstupní zprávu, ale nezpracoval ji; v `false`opačném případě .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Požadavky na systém rozhraní .NET Framework](../../get-started/system-requirements.md).  
  
 **Knihovny dll:**  
  
 V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll ll  
  
 V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční informace k nespravovanému rozhraní API WPF](wpf-unmanaged-api-reference.md)

---
title: LoadFromHistory Function - WPF nespravované rozhraní API odkaz
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141572"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>Funkce LoadFromHistory (WPF Unmanaged API Reference)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno k použití přímo z vašeho kódu.  
  
 Používá infrastrukturu WPF (Windows Presentation Foundation) pro správu systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a>Parametry  
 pHistoryStream  
 Ukazatel na datový proud informací o historii.  
  
 pBindCtx  
 Ukazatel na kontext vazby.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Požadavky na systém rozhraní .NET Framework](../../get-started/system-requirements.md).  
  
 **Knihovny dll:**  
  
 V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll ll  
  
 V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční informace k nespravovanému rozhraní API WPF](wpf-unmanaged-api-reference.md)

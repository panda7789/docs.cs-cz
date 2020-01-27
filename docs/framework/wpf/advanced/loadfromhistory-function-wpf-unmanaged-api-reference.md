---
title: Funkce LoadFromHistory – reference nespravovaného rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 7807e073d1f09ac6a6213aee6d86d53cc75a3c56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727927"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>LoadFromHistory – funkce (Referenční dokumentace rozhraní API nespravovaného subsystému WPF)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno pro použití přímo v kódu.  
  
 Používá se v infrastruktuře Windows Presentation Foundation (WPF) pro správu systému Windows.  
  
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
 **Platformy:** Viz [požadavky na systém .NET Framework](../../get-started/system-requirements.md).  
  
 **DLL**  
  
 V .NET Framework 3,0 a 3,5: PresentationHostDLL. dll  
  
 V .NET Framework 4 a novější: PresentationHost_v0400. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Odkaz na nespravované rozhraní API subsystému WPF](wpf-unmanaged-api-reference.md)

---
title: Funkce SaveToHistory – reference nespravovaného rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 7337e5dc23a3dce5de8270902bce228c49bc6edb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731759"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a>SaveToHistory – funkce (Referenční dokumentace rozhraní API nespravovaného subsystému WPF)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno pro použití přímo v kódu.  
  
 Používá se v infrastruktuře Windows Presentation Foundation (WPF) pro správu systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
## <a name="parameters"></a>Parametry  
 pHistoryStream  
 Ukazatel na datový proud historie.  
  
## <a name="requirements"></a>Požadavky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém .NET Framework](../../get-started/system-requirements.md).  
  
 **DLL**  
  
 V .NET Framework 3,0 a 3,5: PresentationHostDLL. dll  
  
 V .NET Framework 4 a novější: PresentationHost_v0400. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Odkaz na nespravované rozhraní API subsystému WPF](wpf-unmanaged-api-reference.md)

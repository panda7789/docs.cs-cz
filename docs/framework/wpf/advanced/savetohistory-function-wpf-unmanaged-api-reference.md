---
title: Funkce SaveToHistory (WPF nespravovaná referenční dokumentace rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 3f6413558ff1f259e497c6a1c31eb2664f70cc48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053454"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a>Funkce SaveToHistory (WPF nespravovaná referenční dokumentace rozhraní API)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.  
  
 Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.  
  
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
 **Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../get-started/system-requirements.md).  
  
 **DLL:**  
  
 V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll  
  
 V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Odkaz na nespravované rozhraní API subsystému WPF](wpf-unmanaged-api-reference.md)

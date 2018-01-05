---
title: "Funkce LoadFromHistory (WPF nespravované rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: LoadFromHistory
api_location: PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6eca1c30664e381101b6e51c1347341432a042b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>Funkce LoadFromHistory (WPF nespravované rozhraní API)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo z vašeho kódu.  
  
 Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 pHistoryStream  
 Ukazatel na datový proud informace o historii.  
  
 pBindCtx  
 Ukazatel na kontext vazby.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém rozhraní .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **KNIHOVNY DLL:**  
  
 V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll  
  
 V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na nespravované rozhraní API subsystému WPF](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)

---
title: "NukeDownloadedCache – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: NukeDownloadedCache
helpviewer_keywords: NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31d7ba7d5f4a9268ea1e04a4c9f09cd17ebfd5bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache – funkce
Odstraní běžné mezipaměť pro stahování language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v WinError.h.  
  
## <a name="remarks"></a>Poznámky  
 Mezipaměť pro stahování CLR je oblasti, kde jsou uložené sestavení se silným názvem, které jsou staženy z adresy URL pro možné opakované použití.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** knihovna Fusion.dll a Mscorwks.dll. Pomocí knihovna Fusion.dll místo Mscorwks.dll zajistit, na které cílí správnou verzi rozhraní .NET Framework.  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [CreateHistoryReader – funkce](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [GetHistoryFileDirectory – funkce](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

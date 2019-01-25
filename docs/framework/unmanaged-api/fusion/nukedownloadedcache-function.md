---
title: NukeDownloadedCache – funkce
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80891da7d61aa5114d5cc4d8aff4c7ce82020237
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720090"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache – funkce
Odstraní běžné mezipaměť pro stahování language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací standardní kódy chyb modelu COM, jak je definovaný ve WinError.h.  
  
## <a name="remarks"></a>Poznámky  
 Mezipaměť pro stahování CLR je oblast, kde jsou uložené sestavení se silným názvem, které byly staženy z adresy URL pro opakované použití je to možné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** Soubor Fusion.dll a knihovny Mscorwks.dll. Ujistěte se, že můžete cílit na správnou verzi rozhraní .NET Framework pomocí soubor Fusion.dll namísto knihovny Mscorwks.dll.  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [CreateHistoryReader – funkce](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [GetHistoryFileDirectory – funkce](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

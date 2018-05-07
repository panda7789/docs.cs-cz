---
title: GetHistoryFileDirectory – funkce
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bba40acf7bfd20897ece4de285fe7a9175be83e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory – funkce
Načte cestu adresáře historie aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wzDir`  
 [out] Vyrovnávací paměť pro cestu k adresáři historie aplikace.  
  
 `pdwSize`  
 [ve out] Délka vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v souboru WinError.h vedle následující hodnoty.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_INVALIDARG|`wzDir` nebo `pdwSize` má hodnotu null, nebo verze řetězec je nesprávný.|  
  
## <a name="remarks"></a>Poznámky  
 Při úspěšném dokončení `pdwSize` argument je nastaven na délku řetězec cesty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** knihovna Fusion.dll a Mscorwks.dll. Pomocí knihovna Fusion.dll místo Mscorwks.dll zajistit, na které cílí správnou verzi rozhraní .NET Framework.  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [CreateHistoryReader – funkce](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [NukeDownloadedCache – funkce](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

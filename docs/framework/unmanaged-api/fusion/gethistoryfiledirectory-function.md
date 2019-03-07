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
ms.openlocfilehash: 21742881c5aef7384be318297aa3432411c3d57c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479278"
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
  
## <a name="parameters"></a>Parametry  
 `wzDir`  
 [out] Vyrovnávací paměť pro cestu k adresáři aplikace historie.  
  
 `pdwSize`  
 [out v] Délka vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací standardní kódy chyb modelu COM, jak jsou definovány v souboru WinError.h kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_INVALIDARG|`wzDir` nebo `pdwSize` má hodnotu null nebo verze řetězce je nesprávný.|  
  
## <a name="remarks"></a>Poznámky  
 Při úspěšném dokončení `pdwSize` argument je nastaven na délku řetězce cesty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** Soubor Fusion.dll a knihovny Mscorwks.dll. Ujistěte se, že můžete cílit na správnou verzi rozhraní .NET Framework pomocí soubor Fusion.dll namísto knihovny Mscorwks.dll.  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [CreateHistoryReader – funkce](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [NukeDownloadedCache – funkce](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

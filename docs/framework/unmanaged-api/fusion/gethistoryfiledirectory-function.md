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
ms.openlocfilehash: adbbf94dc36c6d82360ed532b283cd666a1a52ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796846"
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory – funkce
Načte cestu k adresáři historie aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wzDir`  
 mimo Vyrovnávací paměť pro uložení cesty k adresáři historie aplikace  
  
 `pdwSize`  
 [in, out] Délka vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací standardní chybové kódy modelu COM, jak jsou definovány v souboru WinError. h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_INVALIDARG|`wzDir`nebo `pdwSize` je null nebo je řetězec verze nesprávný.|  
  
## <a name="remarks"></a>Poznámky  
 Po úspěšném dokončení `pdwSize` je argument nastaven na délku řetězce cesty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Fusion. h  
  
 **Knihovna** Fusion. dll a knihovny Mscorwks. dll. Použijte knihovnu Fusion. dll namísto knihovny Mscorwks. dll, abyste se ujistili, že cílíte na správnou verzi .NET Framework.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [CreateHistoryReader – funkce](createhistoryreader-function.md)
- [NukeDownloadedCache – funkce](nukedownloadedcache-function.md)
- [Globální statické funkce pro fúze](fusion-global-static-functions.md)

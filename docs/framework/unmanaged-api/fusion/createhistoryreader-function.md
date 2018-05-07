---
title: CreateHistoryReader – funkce
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3a3cc21dbbcfa99ddcecb534bd2e337da005597
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader – funkce
Vytvoří historie čtečky zadaný soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `wzFilePath`  
 [v] Cesta k souboru.  
  
 `ppHistoryReader`  
 [out] Při úspěšném dokončení obsahuje ukazatel na historie čtečky.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v WinError.h, kromě hodnot, které jsou popsány v následující tabulce.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Označuje, že metoda byla úspěšně dokončena.|  
|E_INVALIDARG|Určuje, že `wzFilePath` nebo `ppHistoryReader` jsou nastaveny na hodnotu Null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Knihovna:** knihovna Fusion.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

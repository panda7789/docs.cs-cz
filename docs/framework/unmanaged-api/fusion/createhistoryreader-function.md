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
ms.openlocfilehash: 2710d14d6e73879fd17a6b58659463ea205f2384
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795375"
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader – funkce
Vytvoří čtečku historie pro zadaný soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `wzFilePath`  
 pro Cesta k souboru.  
  
 `ppHistoryReader`  
 mimo Po úspěšném dokončení obsahuje ukazatel na čtečku historie.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací standardní chybové kódy modelu COM, jak jsou definovány v WinError. h, kromě hodnot popsaných v následující tabulce.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Označuje, že metoda byla úspěšně dokončena.|  
|E_INVALIDARG|Označuje, `wzFilePath` že `ppHistoryReader` nebo jsou nastaveny na odkaz s hodnotou null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Knihovna** Fusion.dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro fúze](fusion-global-static-functions.md)

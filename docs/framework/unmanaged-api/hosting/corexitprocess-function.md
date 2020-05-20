---
title: CorExitProcess – funkce
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: a60805e1fd78cb14835957a7afc14fe279cb20fb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616564"
---
# <a name="corexitprocess-function"></a>CorExitProcess – funkce
Ukončí aktuální nespravovaný proces.  
  
 Tato funkce se už nepoužívá v .NET Framework 4. Místo toho použijte metodu [ICLRMetaHost:: ExitProcess –](iclrmetahost-exitprocess-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `exitCode`  
 Celé číslo, které určuje ukončovací kód procesu.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Počínaje .NET Framework 4 `CorExitProcess` ukončí každý spuštěný modul runtime v procesu, nikoli jenom modul runtime, ke kterému byly navázány starší verze rozhraní API.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)

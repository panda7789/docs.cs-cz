---
title: _CorExeMain2 – funkce
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
ms.openlocfilehash: cc5324683daa9a02a6a89b2a3fb57ee9fd5dbe72
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136952"
---
# <a name="_corexemain2-function"></a>_CorExeMain2 – funkce
Provede vstupní bod v zadaném kódu mapované paměti. Tato funkce je volána zavaděčem operačního systému.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pUnmappedPE`  
 pro Ukazatel na kód mapované paměti.  
  
 `cUnmappedPE`  
 pro Počet elementů, které `pUnmappedPE` může uchovávat.  
  
 `pImageNameIn`  
 pro Ukazatel na název spustitelného obrázku.  
  
 `pLoadersFileName`  
 pro Název souboru zavaděče.  
  
 `pCmdLine`  
 pro Parametry příkazového řádku, pokud existují.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

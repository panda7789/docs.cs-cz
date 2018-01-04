---
title: "ISymUnmanagedWriter4::GetDebugInfoWithPadding – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f85486370d567ceb1506c41f6aa7c4f3a1929941
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a>ISymUnmanagedWriter4::GetDebugInfoWithPadding – metoda
Funguje stejně jako [getdebuginfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) s tím rozdílem, že řetězec cesty je doplněno nulami následující ukončující znak hodnoty null tak, aby data řetězec pevnou velikost `MAX_PATH`. Odsazení je poskytnuta pouze v případě délka řetězce cesty, samotné je menší než `MAX_PATH`.  
  
 To usnadňuje vytvoření nástrojů pro tento rozdíl PE soubory.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter4 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)

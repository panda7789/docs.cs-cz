---
title: "ISymUnmanagedENCUpdate::UpdateMethodLines – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e8ffecba62b6531c852e6510013ba56b9258b64
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a>ISymUnmanagedENCUpdate::UpdateMethodLines – metoda
Umožňuje aktualizaci řádku informace pro metodu, která nebyla překompilovat, ale jejichž řádky byl přesunut nezávisle. Rozdílové každý příkaz je povolen.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mdMethodToken`  
 [v] Metadata metoda tokenu.  
  
 `pDeltas`  
 [v] Pole `INT32` hodnoty, které označuje rozdíly pro každý bod pořadí v metodě.  
  
 `cDeltas`  
 [v] A `ULONG` obsahující velikost `pDeltas` parametr.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedENCUpdate – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

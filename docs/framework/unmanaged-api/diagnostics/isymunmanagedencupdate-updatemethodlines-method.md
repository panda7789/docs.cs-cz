---
title: ISymUnmanagedENCUpdate::UpdateMethodLines – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 9aace77c4b3549c033433d4c305b07daa1f7a8c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448992"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a>ISymUnmanagedENCUpdate::UpdateMethodLines – metoda
Umožňuje aktualizovat informace o řádku pro metodu, která není znovu zkompilována, ale jejíž řádky byly přesunuty nezávisle. Rozdíl pro každý příkaz je povolen.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a>Parametry  
 `mdMethodToken`  
 pro Metadata tokenu metody.  
  
 `pDeltas`  
 pro Pole hodnot `INT32`, které označují rozdílové hodnoty pro každý bod sekvence v metodě.  
  
 `cDeltas`  
 pro `ULONG`, který obsahuje velikost `pDeltas` parametru.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedENCUpdate – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

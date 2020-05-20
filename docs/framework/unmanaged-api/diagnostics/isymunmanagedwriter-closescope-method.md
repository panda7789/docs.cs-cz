---
title: ISymUnmanagedWriter::CloseScope – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
ms.openlocfilehash: 4d8790dc68bc063deed4c58ba0df8e9ea258b9d7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610077"
---
# <a name="isymunmanagedwriterclosescope-method"></a>ISymUnmanagedWriter::CloseScope – metoda
Zavře aktuální lexikální obor.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a>Parametry  
 `endOffset`  
 pro Posun od začátku metody bodu na konci poslední instrukce v lexikálním oboru v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Jakmile je obor uzavřen, nelze v něm definovat žádné další proměnné.  
  
 [ISymUnmanagedWriter:: OpenScope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) vrátí neprůhledný identifikátor oboru, který lze použít s [ISymUnmanagedWriter:: SetScopeRange –](isymunmanagedwriter-setscoperange-method.md) pro pozdější definování počátečního a koncového posunu oboru. V tomto případě jsou posunutí předaná do `ISymUnmanagedWriter::OpenScope` a `ISymUnmanagedWriter::CloseScope` ignorována. Identifikátory oboru jsou platné pouze v aktuální metodě.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)

---
title: ISymUnmanagedScope::GetEndOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: 25a8188e3ab62c095355b72b3e63e767a6768114
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446352"
---
# <a name="isymunmanagedscopegetendoffset-method"></a>ISymUnmanagedScope::GetEndOffset – metoda
Gets the end offset for this scope.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] A pointer to a `ULONG32` that receives the end offset.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Požadavky  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedScope – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [GetStartOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)

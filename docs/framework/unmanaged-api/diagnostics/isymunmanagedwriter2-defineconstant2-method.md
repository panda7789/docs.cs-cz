---
title: ISymUnmanagedWriter2::DefineConstant2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
ms.openlocfilehash: 6600ca7e70ac77ffba0c75812f27d388c354ece6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438325"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a>ISymUnmanagedWriter2::DefineConstant2 – metoda
Defines a name for a constant value.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 [in] The constant name.  
  
 `value`  
 [in] The value of the constant.  
  
 `sigToken`  
 [in] The metadata token of the constant.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Požadavky  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [DefineConstant – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)

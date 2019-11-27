---
title: ISymUnmanagedWriter::OpenScope – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
ms.openlocfilehash: 915b05d0d2ac611678fdcc94dd42bbb1962e6ceb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427894"
---
# <a name="isymunmanagedwriteropenscope-method"></a>ISymUnmanagedWriter::OpenScope – metoda
Otevře nový lexikální obor v aktuální metodě. Rozsah se projeví jako nový aktuální obor a je vložen do zásobníku oborů. Obory musí tvořit hierarchii. Na stejné úrovni není dovoleno překrývat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `startOffset`  
 pro Posun první instrukce v lexikálním rozsahu, v bajtech, od začátku metody.  
  
 `pRetVal`  
 mimo Ukazatel na `ULONG32`, který přijímá identifikátor oboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 `ISymUnmanagedWriter::OpenScope` vrací neprůhledný identifikátor oboru, který lze použít s [ISymUnmanagedWriter:: SetScopeRange –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) k definování počátečního a koncového posunu oboru v pozdějším čase. V tomto případě jsou posuny předané `ISymUnmanagedWriter::OpenScope` a [ISymUnmanagedWriter:: CloseScope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) ignorovány. Identifikátory oboru jsou platné pouze v aktuální metodě.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

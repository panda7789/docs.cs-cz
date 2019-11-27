---
title: ISymUnmanagedWriter::SetScopeRange – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
ms.openlocfilehash: b404a187d8628a04d2aa51df15f86fcc9d0b14f8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427855"
---
# <a name="isymunmanagedwritersetscoperange-method"></a>ISymUnmanagedWriter::SetScopeRange – metoda
Definuje rozsah posunu pro zadaný lexikální obor. Rozsah se projeví jako nový aktuální obor a je vložen do zásobníku oborů. Obory musí tvořit hierarchii. Na stejné úrovni není dovoleno překrývat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a>Parametry  
 `scopeId`  
 pro Identifikátor oboru pro obor.  
  
 `startOffset`  
 pro Posun v bajtech první instrukce v lexikálním rozsahu od začátku metody.  
  
 `endOffset`  
 pro Posun poslední instrukce v lexikálním oboru od začátku metody v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 [ISymUnmanagedWriter:: OpenScope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) vrátí neprůhledný identifikátor oboru, který lze použít s `ISymUnmanagedWriter::SetScopeRange` k definování počátečního a koncového posunu oboru později. V tomto případě jsou posuny předané `ISymUnmanagedWriter::OpenScope` a [ISymUnmanagedWriter:: CloseScope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) ignorovány. Identifikátory oboru jsou platné pouze v aktuální metodě.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

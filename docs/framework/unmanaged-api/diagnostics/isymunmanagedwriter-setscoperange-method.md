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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d7fe8f36c7a5dbe6e715402fd7253092b64e68e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078964"
---
# <a name="isymunmanagedwritersetscoperange-method"></a>ISymUnmanagedWriter::SetScopeRange – metoda
Definuje rozsah pro zadaný obor lexikální posunu. Obor se stane novou aktuální obor a vloženo do zásobníku oborů. Obory musí tvořit hierarchii. Na stejné úrovni nemohou překrývat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a>Parametry  
 `scopeId`  
 [in] Identifikátor rozsahu pro obor.  
  
 `startOffset`  
 [in] Posun v bajtech, první instrukce v lexikálním rozsahu od začátku metody.  
  
 `endOffset`  
 [in] Posun v bajtech, která je poslední instrukce v lexikálním rozsahu od začátku metody.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 [Isymunmanagedwriter::openscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) vrátí neprůhledný oboru identifikátor, který lze použít s `ISymUnmanagedWriter::SetScopeRange` a určete obor je počáteční a koncové posunutí později. V takovém případě posunutí předán `ISymUnmanagedWriter::OpenScope` a [isymunmanagedwriter::closescope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) jsou ignorovány. Identifikátory obor platí pouze v aktuální metodě.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

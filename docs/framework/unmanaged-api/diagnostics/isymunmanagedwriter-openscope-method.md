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
ms.openlocfilehash: 4008b2a7d785781da5f35b3dc1e564487cb8e760
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609778"
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
 mimo Ukazatel na `ULONG32` , který přijímá identifikátor oboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 `ISymUnmanagedWriter::OpenScope`Vrátí neprůhledný identifikátor oboru, který lze použít s [ISymUnmanagedWriter:: SetScopeRange –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) k definování počátečního a koncového posunu oboru v pozdějším čase. V tomto případě jsou posunutí předaná do `ISymUnmanagedWriter::OpenScope` a [ISymUnmanagedWriter:: CloseScope –](isymunmanagedwriter-closescope-method.md) ignorována. Identifikátory oboru jsou platné pouze v aktuální metodě.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)

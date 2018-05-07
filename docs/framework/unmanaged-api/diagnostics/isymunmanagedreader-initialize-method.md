---
title: ISymUnmanagedReader::Initialize – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d141d23f02b2abc92e3d4455aebe1a4057b6bb85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize – metoda
Inicializuje čtečky symbol s rozhraním program pro import metadat, které bude tato čtečky spojený s, spolu s názvem souboru modulu.  
  
> [!NOTE]
>  Tuto metodu lze volat pouze jednou a musí být volána před provedením další metody čtečky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a>Parametry  
 `importer`  
 [v] Rozhraní – Importér metadata, pomocí kterého bude tento čtečky spojený.  
  
 `filename`  
 [v] Název souboru modulu. Můžete použít `pIStream` parametr místo.  
  
 `searchPath`  
 [v] Cesta k vyhledávání. Tento parametr je volitelný.  
  
 `pIStream`  
 [v] Proud souboru použít jako alternativu k parametr filename.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Je třeba zadat pouze jeden z `filename` nebo `pIStream` parametry, nikoli oba dva. `searchPath` Parametr je nepovinný.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

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
ms.openlocfilehash: 1a5eb91d02ce55601f86dcadc744ef23ca430d9c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471690"
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize – metoda
Inicializuje modul pro načítání symbolů rozhraní programu pro import metadat, která tento čtecí bude spojená s, spolu s názvem souboru modulu.  
  
> [!NOTE]
>  Tuto metodu lze volat pouze jednou a musí být volána před všechny ostatní metody čtečky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a>Parametry  
 `importer`  
 [in] Rozhraní programu pro import metadat se kterým bude tento čtecí spojená.  
  
 `filename`  
 [in] Název souboru modulu. Můžete použít `pIStream` parametr místo.  
  
 `searchPath`  
 [in] Cesta pro vyhledávání. Tento parametr je volitelný.  
  
 `pIStream`  
 [in] Soubor datového proudu, používá jako alternativu k parametr filename.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Je třeba zadat pouze jeden z `filename` nebo `pIStream` parametrů, ne obojí. `searchPath` Parametr je nepovinný.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

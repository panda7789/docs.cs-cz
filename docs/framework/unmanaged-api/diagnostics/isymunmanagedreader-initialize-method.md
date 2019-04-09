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
ms.openlocfilehash: 661c27b9c21f77104b8a86163d3c92d44f8a85df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181776"
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

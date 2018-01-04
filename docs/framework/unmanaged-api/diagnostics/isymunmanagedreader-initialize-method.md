---
title: "ISymUnmanagedReader::Initialize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 433cd62f7801d386f3b34b7fc8e95bd1d0c5f765
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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

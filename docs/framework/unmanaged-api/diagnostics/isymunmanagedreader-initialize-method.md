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
ms.openlocfilehash: 07d2de5d12fd769cb5cce243d9e721bb6fc185a7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615472"
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize – metoda
Inicializuje čtečku symbolů pomocí rozhraní pro import metadat, ke kterému bude tento čtenář přidružen, společně s názvem souboru modulu.  
  
> [!NOTE]
> Tuto metodu lze volat pouze jednou a je třeba ji volat před všemi jinými metodami čtenáře.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a>Parametry  
 `importer`  
 pro Rozhraní pro import metadat, ke kterému se bude tento čtenář přidružit.  
  
 `filename`  
 pro Název souboru modulu. Místo toho můžete použít `pIStream` parametr.  
  
 `searchPath`  
 pro Cesta, která se má vyhledat Tento parametr je volitelný.  
  
 `pIStream`  
 pro Datový proud souboru, který se používá jako alternativa k parametru filename.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Je nutné zadat pouze jeden z `filename` `pIStream` parametrů nebo, nikoli obojí. `searchPath`Parametr je nepovinný.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedReader – rozhraní](isymunmanagedreader-interface.md)

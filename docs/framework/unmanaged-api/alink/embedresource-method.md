---
title: EmbedResource – metoda
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af5a200578c34464b5f8d86e568d08d814b46a29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742156"
---
# <a name="embedresource-method"></a>EmbedResource – metoda
Deklaruje vložený prostředek. Tato metoda není ve skutečnosti vložit prostředek.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení.  
  
 `FileToken`  
 Soubor tokenu nebo sestavení ID souboru, který obsahuje prostředek.  
  
 `pszResourceName`  
 Název prostředku.  
  
 `dwOffset`  
 Posun prostředku z adresu RVA.  
  
 `dwFlags`  
 Usnadnění označí jako `mrPublic` a `mrPrivate`. Mohou být předány tyto příznaky [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje, vrátí hodnotu S_OK.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h.  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)

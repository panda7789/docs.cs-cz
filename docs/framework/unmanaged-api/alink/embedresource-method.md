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
ms.openlocfilehash: eb1fc266c8451953c8b6a9c686f4a1c1951966e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="embedresource-method"></a>EmbedResource – metoda
Deklaruje vložený prostředek. Tato metoda není ve skutečnosti vložit prostředek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení.  
  
 `FileToken`  
 Soubor ID souboru, který obsahuje prostředek token nebo sestavení.  
  
 `pszResourceName`  
 Název prostředku.  
  
 `dwOffset`  
 Posun prostředku z RVA.  
  
 `dwFlags`  
 Usnadnění flags – například `mrPublic` a `mrPrivate`. Může být předány tyto příznaky [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h.  
  
## <a name="see-also"></a>Viz také  
 [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)

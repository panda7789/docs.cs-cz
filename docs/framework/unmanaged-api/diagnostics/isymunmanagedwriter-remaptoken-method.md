---
title: ISymUnmanagedWriter::RemapToken – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
ms.openlocfilehash: 53cc908e0dc8cc5cc980ec365ccac0df4e620cac
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609765"
---
# <a name="isymunmanagedwriterremaptoken-method"></a>ISymUnmanagedWriter::RemapToken – metoda
Upozorní zapisovač symbolů, že token metadat byl přemapován, protože byla vygenerována metadata. Pokud zapisovač symbolů uložil starý token do úložiště symbolů, musí buď aktualizovat uložený token s novou hodnotou, nebo musí uložit mapu pro odpovídající čtečku symbolů k přemapování během fáze čtení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a>Parametry  
 `oldToken`  
 pro Token metadat, který byl přemapován.  
  
 `newToken`  
 pro Nový token metadat, ke kterému `oldToken` bylo přemapováno.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)

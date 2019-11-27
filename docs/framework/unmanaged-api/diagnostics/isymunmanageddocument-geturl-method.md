---
title: ISymUnmanagedDocument::GetURL – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
ms.openlocfilehash: 134a89d62a0fc455a9579de1e577103f1fe6abcf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449119"
---
# <a name="isymunmanageddocumentgeturl-method"></a>ISymUnmanagedDocument::GetURL – metoda
Vrátí adresu URL (Uniform Resource Locator) pro tento dokument.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchUrl`  
 pro Velikost vyrovnávací paměti `szURL` v znacích.  
  
 `pcchUrl`  
 mimo Ukazatel na proměnnou, která přijímá velikost adresy URL, včetně ukončení hodnoty null.  
  
 `szUrl`  
 mimo Vyrovnávací paměť obsahující adresu URL.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě kód chyby.  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedDocument – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

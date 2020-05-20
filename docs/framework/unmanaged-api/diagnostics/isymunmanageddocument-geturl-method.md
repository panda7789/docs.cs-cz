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
ms.openlocfilehash: 3685707f1983ffec413e9cea2df5034ac53f643a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615589"
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
 pro Velikost `szURL` vyrovnávací paměti ve znacích.  
  
 `pcchUrl`  
 mimo Ukazatel na proměnnou, která přijímá velikost adresy URL, včetně ukončení hodnoty null.  
  
 `szUrl`  
 mimo Vyrovnávací paměť obsahující adresu URL.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě kód chyby.  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedDocument – rozhraní](isymunmanageddocument-interface.md)

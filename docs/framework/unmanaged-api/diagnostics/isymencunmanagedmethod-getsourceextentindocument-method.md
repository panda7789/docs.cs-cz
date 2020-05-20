---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
ms.openlocfilehash: 3ac8bb3a20ce82b734a572832a9cbb75fa2568c4
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441900"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a>ISymENCUnmanagedMethod::GetSourceExtentInDocument – metoda
Získá nejmenší počáteční řádek a největšího koncového řádku pro metodu v konkrétním dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a>Parametry  
 `document`  
 pro Ukazatel na dokument.  
  
 `pstartLine`  
 mimo Ukazatel na `ULONG32` , který obdrží počáteční řádek.  
  
 `pendLine`  
 mimo Ukazatel na `ULONG32` , který získá koncovou čáru.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymENCUnmanagedMethod – rozhraní](isymencunmanagedmethod-interface.md)

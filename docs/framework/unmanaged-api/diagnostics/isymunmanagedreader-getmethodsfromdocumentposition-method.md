---
title: "ISymUnmanagedReader::GetMethodsFromDocumentPosition – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdf3762c40e5ec4da84a27ed7abcb15981b81379
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a>ISymUnmanagedReader::GetMethodsFromDocumentPosition – metoda
Vrátí pole metod, z nichž každý obsahuje zarážek na dané pozici v dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `document`  
 [v] Zadaný dokument.  
  
 `line`  
 [v] Řádku zadaný dokument.  
  
 `column`  
 [v] Sloupec zadaný dokument.  
  
 `cMethod`  
 [v] Velikost `pRetVal` pole.  
  
 `pcMethod`  
 [out] Ukazatel na proměnnou, která přijímá počet elementů, vrátí se v `pRetVal` pole.  
  
 `pRetVal`  
 [out] Ukazatele, každý z nich odkazuje na pole [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objekt, který reprezentuje metodu obsahující bod přerušení.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

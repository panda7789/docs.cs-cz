---
title: "ISymUnmanagedReader2::GetMethodsInDocument – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetMethodsInDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 175ab55c849a1457cafc46b29d67e5d22a42ee6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a>ISymUnmanagedReader2::GetMethodsInDocument – metoda
Získá každých metoda, která obsahuje informace o řádku v zadané dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `document`  
 [v] Ukazatel na dokumentu.  
  
 `cMethod`  
 [v] A `ULONG32` určující velikost `pRetVal` pole.  
  
 `pcMethod`  
 [out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat metody.  
  
 `pRetVal`  
 [out] Ukazatel do vyrovnávací paměti, která přijímá metody.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedReader2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

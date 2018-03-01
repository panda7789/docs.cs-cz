---
title: "ISymENCUnmanagedMethod::GetLineFromOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 535c0310a3220c5691f26c9081f6d2f747196e91
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset – metoda
Získá související s posunem informace řádku. Pokud parametr posunutí (`dwOffset`) není bod sekvence, tato metoda získá řádku informace spojené s posunem od předchozí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwOffset`  
 [v] A `ULONG32` obsahující posun.  
  
 `pline`  
 [out] Ukazatel na `ULONG32` která přijme řádku.  
  
 `pcolumn`  
 [out] Ukazatel na `ULONG32` která přijme sloupci.  
  
 `pendLine`  
 [out] Ukazatel na `ULONG32` která přijme na konci řádku.  
  
 `pendColumn`  
 [out] Ukazatel na `ULONG32` která přijme sloupec end.  
  
 `pdwStartOffset`  
 [out] Ukazatel na `ULONG32` která přijme bodem přidružené pořadí.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymENCUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

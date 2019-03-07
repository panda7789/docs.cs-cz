---
title: ISymENCUnmanagedMethod::GetLineFromOffset – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90d993bc6b947d309ce1a0fb10ad231a429be567
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471911"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset – metoda
Získá informace o řádku, které jsou spojené s posunem. Pokud parametr offset (`dwOffset`) není bod sekvence, tato metoda získá informace o řádku spojené s předchozím posunu.  
  
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
  
## <a name="parameters"></a>Parametry  
 `dwOffset`  
 [in] A `ULONG32` obsahující posun.  
  
 `pline`  
 [out] Ukazatel `ULONG32` , která obdrží řádku.  
  
 `pcolumn`  
 [out] Ukazatel `ULONG32` , která obdrží sloupci.  
  
 `pendLine`  
 [out] Ukazatel `ULONG32` , který přijímá na konci řádku.  
  
 `pendColumn`  
 [out] Ukazatel `ULONG32` , která obdrží koncový sloupec.  
  
 `pdwStartOffset`  
 [out] Ukazatel `ULONG32` , která obdrží bodu sekvence. přidružené.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymENCUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

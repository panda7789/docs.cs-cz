---
title: "ISymUnmanagedMethod::GetSourceStartEnd – metoda"
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
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2bdc044d4560b616bd6eeb8d642567add1f659f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a>ISymUnmanagedMethod::GetSourceStartEnd – metoda
Získá počáteční a koncové pozice dokumentu pro zdroj této metody. První pozice pole je spuštění a druhý pozice pole je end.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `docs`  
 [v] Počáteční a koncovou zdroj dokumenty.  
  
 `lines`  
 [v] Počáteční a koncovou řádky do odpovídajícího zdroje dokumenty.  
  
 `columns`  
 [v] Počáteční a koncovou sloupce do odpovídajícího zdroje dokumenty.  
  
 `pRetVal`  
 [out] `true` kdyby pozic definován; jinak hodnota `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

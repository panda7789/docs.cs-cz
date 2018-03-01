---
title: "ISymUnmanagedNamespace::GetVariables – metoda"
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
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1fcfeba065bcdc996b5bc742dfea33b4417a29f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagednamespacegetvariables-method"></a>ISymUnmanagedNamespace::GetVariables – metoda
Vrátí všechny proměnné definované v globálním oboru v rámci tento obor názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cVars`  
 [v] A `ULONG32` určující velikost `pVars` pole.  
  
 `pcVars`  
 [out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat obory názvů.  
  
 `pVars`  
 [out] Ukazatel na vyrovnávací paměť, která obsahuje obory názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedNamespace – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

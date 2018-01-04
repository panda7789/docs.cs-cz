---
title: "ISymUnmanagedWriter::SetUserEntryPoint – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetUserEntryPoint
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5da021bce46df02789547eb7ee50133b6f4d4af6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a>ISymUnmanagedWriter::SetUserEntryPoint – metoda
Určuje metodu definovaný uživatelem, která je vstupní bod pro tento modul. Hlavní metody uživatele místo generované kompilátorem zástupných procedur před hlavním může být například tento vstupní bod.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a>Parametry  
 `entryMethod`  
 [v] Bod token metadata pro metody, které se vstup uživatele.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

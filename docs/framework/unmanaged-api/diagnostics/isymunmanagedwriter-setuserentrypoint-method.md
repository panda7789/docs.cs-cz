---
title: ISymUnmanagedWriter::SetUserEntryPoint – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3bd3d411ad6fe7f65d1eeb25754794704752009e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488354"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a>ISymUnmanagedWriter::SetUserEntryPoint – metoda
Určuje metodu definovaný uživatelem, která je vstupním bodem pro tento modul. Tento vstupní bod může být například hlavní metoda uživatele místo vygenerovaný kompilátorem zástupné procedury před hlavní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a>Parametry  
 `entryMethod`  
 [in] Bodu tokenu metadat pro metodu, která je vstup uživatele.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

---
title: ISymUnmanagedWriter::DefineParameter – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b552ef39c7f73aaa5cfeae4a313e329b267abf98
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643385"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a>ISymUnmanagedWriter::DefineParameter – metoda
Definuje jeden parametr v aktuální metodě. Typ parametru je převzata z pozice parametru (pořadí) v podpisu metody.  
  
 Pokud parametry jsou definované v metadatech pro dané metody, není nutné znovu definovat pomocí této metody. Čtenáři symbolu, musíte zaškrtnout běžná metadata pro parametry před vrácením se změnami úložiště symbolů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 [in] Název parametru.  
  
 `attributes`  
 [in] Atributy parametru.  
  
 `sequence`  
 [in] Podpis parametru.  
  
 `addrKind`  
 [in] Typ adresy.  
  
 `addr1`  
 [in] První adresa pro specifikaci parametru.  
  
 `addr2`  
 [in] Druhý adresa pro specifikaci parametru.  
  
 `addr3`  
 [in] Je třetí adresa pro specifikaci parametru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

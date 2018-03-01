---
title: "ISymUnmanagedWriter::GetDebugInfo – metoda"
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
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f071bfe88397d6431fb50403c3969d82c5cfe8fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo – metoda
Vrací informace potřebné pro kompilátor zapsat záznam adresáře ladění přenosné hlavičky spustitelného souboru (PE). Zapisovač symbol vyplní všechna pole s výjimkou `TimeDateStamp` a `PointerToRawData`. (Kompilátor je zodpovědná za správně nastavení těchto dvou polích.)  
  
 Kompilátor by měly volat tuto metodu, emitování datový objekt blob do souboru PE, nastavte `PointerToRawData` pole IMAGE_DEBUG_DIRECTORY přejděte emitovaného data a IMAGE_DEBUG_DIRECTORY k zápisu do souboru PE. Kompilátor nastavte také `TimeDateStamp` pole, aby se rovnala `TimeDateStamp` souboru PE generován.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pIDD`  
 [ve out] Ukazatel IMAGE_DEBUG_DIRECTORY, který vyplní zapisovače symbol.  
  
 `cData`  
 [v] A `DWORD` obsahující velikost dat ladění.  
  
 `pcData`  
 [out] Ukazatel na `DWORD` která přijme velikost vyrovnávací paměti musí obsahovat data ladění.  
  
 `data`  
 [out] Ukazatel na vyrovnávací paměť, která je dostatečně velký pro uložení dat ladění pro úložiště symbolů.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

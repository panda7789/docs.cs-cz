---
title: "ISymUnmanagedWriter::Initialize – metoda"
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
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 737e6b5218d51d8a1a051104ecdd11240a2ddac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize – metoda
Nastaví rozhraní vysílače metadata, pomocí kterého bude tento zapisovač spojený a název výstupního souboru, ke kterému se zapíšou symboly pro ladění.  
  
 Tuto metodu lze volat pouze jednou a musí být voláno před jiné metody zapisovače. Název souboru může vyžadovat některé zapisovače. Název souboru však můžete vždy předat této metodě bez negativnímu vlivu na zapisovačů, které nepoužívají název souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a>Parametry  
 `emitter`  
 [v] Ukazatel rozhraní vysílače metadat.  
  
 `filename`  
 [v] Název souboru, do které se zapisují symboly pro ladění. Pokud název souboru je zadán pro zapisovač, který nepoužívá názvy souborů, tento parametr je ignorován.  
  
 `pIStream`  
 [v] -Li zadána, bude zapisovače symbol emitování symboly do danou <xref:System.Runtime.InteropServices.ComTypes.IStream> spíše než do zadaného v souboru `filename` parametr. `pIStream` Parametr je nepovinný.  
  
 `fFullBuild`  
 [v] `true` Pokud je to úplné opětovné sestavení; `false` Pokud je to přírůstkové kompilace.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Initialize2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)

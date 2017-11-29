---
title: "ISymUnmanagedWriter::Initialize2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e76543c35a717b95ae37985648986abaf16bf85d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2 – metoda
Nastaví rozhraní vysílače metadata, pomocí kterého bude tento zapisovač spojený a název výstupního souboru, ke kterému se zapíšou symboly pro ladění. Tato metoda také umožňuje nastavit konečného umístění souboru databáze (PDB).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
#### <a name="parameters"></a>Parametry  
 `emitter`  
 [v] Ukazatel rozhraní vysílače metadat.  
  
 `tempfilename`  
 [v] Ukazatel na `WCHAR` obsahující název souboru, do které se zapisují symboly pro ladění. Pokud název souboru je zadán pro zapisovač, který nepoužívá názvy souborů, tento parametr je ignorován.  
  
 `pIStream`  
 [v] -Li zadána, zapisovač symbol vysílá symboly do danou <xref:System.Runtime.InteropServices.ComTypes.IStream> spíše než do zadaného v souboru `filename` parametr. `pIStream` Parametr je nepovinný.  
  
 `fFullBuild`  
 [v] `true` Pokud je to úplné opětovné sestavení; `false` Pokud je to přírůstkové kompilace.  
  
 `finalfilename`  
 [v] Ukazatel na `WCHAR` tedy řetězec cesty do konečného umístění souboru PDB.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Initialize – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)

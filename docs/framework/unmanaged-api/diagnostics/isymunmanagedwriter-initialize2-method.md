---
title: ISymUnmanagedWriter::Initialize2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71eeeefc594c450d5fb95ebae17e3c1316301278
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481375"
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2 – metoda
Nastaví rozhraní vysílače metadat, díky které bude tento zapisovač přidružené a nastaví název výstupního souboru, do kterého budou zapsány symboly ladění. Tato metoda také umožňuje nastavit konečné umístění souboru databáze (PDB) programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a>Parametry  
 `emitter`  
 [in] Ukazatel na rozhraní vysílače metadat.  
  
 `tempfilename`  
 [in] Ukazatel `WCHAR` , který obsahuje název souboru, do kterého se zapisují symboly ladění. Pokud je název souboru zadaný pro zapisovače, který nepoužívá názvy souborů, tento parametr je ignorován.  
  
 `pIStream`  
 [in] Pokud zadaná, zapisovač symbol vydává symboly do dané <xref:System.Runtime.InteropServices.ComTypes.IStream> , nikoli do souboru zadaného v `filename` parametr. `pIStream` Parametr je nepovinný.  
  
 `fFullBuild`  
 [in] `true` Pokud se jedná úplné opětovné sestavení; `false` Pokud přírůstková kompilace.  
  
 `finalfilename`  
 [in] Ukazatel `WCHAR` řetězec cesty, který je do konečného umístění souboru PDB.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Initialize – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)

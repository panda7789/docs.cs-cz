---
title: ISymUnmanagedWriter::Initialize – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 417cf623948d16147f9a1242d714f4df1311a314
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212047"
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize – metoda
Nastaví rozhraní vysílače metadat, díky které bude tento zapisovač přidružené a nastaví název výstupního souboru, do kterého budou zapsány symboly ladění.  
  
 Tuto metodu lze volat pouze jednou a musí být volána před všechny ostatní metody zapisovače. Někteří uživatelé vytvářející obsah mohou vyžadovat název souboru. Název souboru však můžete vždy předat této metodě bez jakékoli negativní vliv na zapisovačů, které se nepoužívá název souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a>Parametry  
 `emitter`  
 [in] Ukazatel na rozhraní vysílače metadat.  
  
 `filename`  
 [in] Název souboru, do kterého se zapisují symboly ladění. Pokud je název souboru zadaný pro zapisovače, který nepoužívá názvy souborů, tento parametr je ignorován.  
  
 `pIStream`  
 [in] Je-li zadána, zapisovač symbol bude generovat symboly do dané <xref:System.Runtime.InteropServices.ComTypes.IStream> , nikoli do souboru zadaného v `filename` parametr. `pIStream` Parametr je nepovinný.  
  
 `fFullBuild`  
 [in] `true` Pokud se jedná úplné opětovné sestavení; `false` Pokud přírůstková kompilace.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Initialize2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)

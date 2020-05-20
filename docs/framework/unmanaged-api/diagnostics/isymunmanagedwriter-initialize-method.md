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
ms.openlocfilehash: 1553e616f60b4f05c06b6457d47454dfb4bc2eb7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614770"
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize – metoda
Nastaví rozhraní Emit metadat, ke kterému bude tento zapisovač přidružen, a nastaví název výstupního souboru, do kterého budou zapsány symboly ladění.  
  
 Tuto metodu lze volat pouze jednou a musí být volána před všemi jinými metodami zapisovače. Některé zapisovače můžou vyžadovat název souboru. K této metodě ale můžete vždy předat název souboru bez negativního vlivu na zapisovače, které nepoužívají název souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a>Parametry  
 `emitter`  
 pro Ukazatel na rozhraní Emit metadat.  
  
 `filename`  
 pro Název souboru, do kterého jsou zapsány symboly ladění. Pokud je název souboru zadán pro zapisovač, který nepoužívá názvy souborů, tento parametr je ignorován.  
  
 `pIStream`  
 pro Je-li tento parametr zadán, zapisovač symbolů bude generovat symboly <xref:System.Runtime.InteropServices.ComTypes.IStream> namísto souboru zadaného v `filename` parametru. `pIStream`Parametr je nepovinný.  
  
 `fFullBuild`  
 [in] `true` Pokud se jedná o úplné opětovné sestavení; `false`Pokud se jedná o přírůstkovou kompilaci.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)
- [Initialize2 – metoda](isymunmanagedwriter-initialize2-method.md)

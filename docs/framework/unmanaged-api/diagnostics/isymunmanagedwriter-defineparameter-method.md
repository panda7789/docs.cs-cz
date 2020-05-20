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
ms.openlocfilehash: c695aa80ea3bf90a29ce7c5d11eda7fae5fe7b2d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614809"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a>ISymUnmanagedWriter::DefineParameter – metoda
Definuje jeden parametr v aktuální metodě. Typ parametru je přijímán z pozice parametru (Sequence) v rámci signatury metody.  
  
 Pokud jsou parametry definovány v metadatech pro danou metodu, nemusíte je znovu definovat pomocí této metody. Čtečky symbolů musí před kontrolou úložiště symbolů zkontrolovat běžná metadata pro parametry.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 pro Název parametru.  
  
 `attributes`  
 pro Atributy parametru.  
  
 `sequence`  
 pro Signatura parametru  
  
 `addrKind`  
 pro Typ adresy.  
  
 `addr1`  
 pro První adresa specifikace parametru.  
  
 `addr2`  
 pro Druhá adresa specifikace parametru.  
  
 `addr3`  
 pro Třetí adresa specifikace parametru.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)

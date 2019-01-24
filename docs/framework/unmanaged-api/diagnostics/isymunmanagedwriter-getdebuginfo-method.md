---
title: ISymUnmanagedWriter::GetDebugInfo – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87dd256bfe8a067ad798bff77a172b936f2d6aab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649931"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo – metoda
Vrací informace nezbytné pro kompilátor zapsat záznam adresáře ladění přenosný spustitelný soubor hlavičky souboru (PE). Zapisovač symbol vyplní všechna pole s výjimkou `TimeDateStamp` a `PointerToRawData`. (Kompilátor je zodpovědný za nastavení těchto dvou polích odpovídajícím způsobem.)  
  
 Kompilátor by měla volat tuto metodu, generování datový objekt blob do souboru PE, nastavte `PointerToRawData` pole IMAGE_DEBUG_DIRECTORY přejděte emitovaný data a zápis IMAGE_DEBUG_DIRECTORY do souboru PE. Kompilátor by měl také nastavit `TimeDateStamp` pole tak, aby odpovídal `TimeDateStamp` generování souboru PE.  
  
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
 [out v] Ukazatel na IMAGE_DEBUG_DIRECTORY, který vyplní zapisovač symbol.  
  
 `cData`  
 [in] A `DWORD` , který obsahuje množství dat ladění.  
  
 `pcData`  
 [out] Ukazatel `DWORD` , která obdrží velikost vyrovnávací paměti musí obsahovat data ladění.  
  
 `data`  
 [out] Ukazatel do vyrovnávací paměti, který je dostatečně velký pro uložení data ladění pro úložiště symbolů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

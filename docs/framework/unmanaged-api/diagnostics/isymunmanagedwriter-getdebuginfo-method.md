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
ms.openlocfilehash: 2b901a3dac499f1ce3f843c59122dd8fd5022147
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427961"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo – metoda
Vrátí informace, které jsou nezbytné pro kompilátor pro zápis položky adresáře ladění v hlavičce přenositelného spustitelného souboru (PE). Zapisovač symbolů vyplní všechna pole s výjimkou `TimeDateStamp` a `PointerToRawData`. (Kompilátor je zodpovědný za správné nastavení těchto dvou polí.)  
  
 Kompilátor by měl zavolat tuto metodu, vygenerovat datový objekt blob do souboru PE, nastavit `PointerToRawData` pole v IMAGE_DEBUG_DIRECTORY tak, aby odkazoval na vygenerovaná data, a zapsat IMAGE_DEBUG_DIRECTORY do souboru PE. Kompilátor by měl také nastavit pole `TimeDateStamp` tak, aby se rovnala `TimeDateStamp` generovaného souboru PE.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `pIDD`  
 [in, out] Ukazatel na IMAGE_DEBUG_DIRECTORY, který zapisovač symbolů vyplní.  
  
 `cData`  
 pro `DWORD`, který obsahuje velikost ladicích dat.  
  
 `pcData`  
 mimo Ukazatel na `DWORD`, který přijímá velikost vyrovnávací paměti, která je nutná k uložení ladicích dat.  
  
 `data`  
 mimo Ukazatel na vyrovnávací paměť, která je dostatečně velká pro ukládání dat ladění pro úložiště symbolů.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

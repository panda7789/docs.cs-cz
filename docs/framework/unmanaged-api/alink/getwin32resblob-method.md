---
title: GetWin32ResBlob – metoda
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
ms.openlocfilehash: ff3103a46390c880a56ff443bfe20744f2ba0bfd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430687"
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob – metoda
Načte objekt BLOB prostředku Win32. Po nastavení možností sestavení volejte tuto metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení  
  
 `FileToken`  
 Token souboru, který se používá k načtení názvu souboru, který se má použít při vytváření prostředku verze Win32  
  
 `fDll`  
 TRUE, pokud je soubor DLL, false pro EXE.  
  
 `pszIconFile`  
 Volitelná ikona, která se má vložit do objektu BLOB prostředku  
  
 `ppResBlob`  
 Přijímá objekt BLOB prostředku.  
  
 `pcbResBlob`  
 Přijímá velikost objektu BLOB.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)

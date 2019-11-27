---
title: SetManifestFile – metoda
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
ms.openlocfilehash: df97f4c37d8f335ce183685debd7c0933be910ed
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445557"
---
# <a name="setmanifestfile-method"></a>SetManifestFile – metoda
Umožňuje určit nebo obnovit soubor manifestu, který Linker používá při vytváření sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFile`  
  
 Název souboru manifestu, jehož obsah je umístěn do objektu BLOB prostředků Win32.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="remarks"></a>Poznámky  
 Před dotazem na Win32ResBlobu tento hovor zavolejte. Hodnota parametru `pszFile` je název souboru manifestu, jehož obsah je čten a umístěn do prostředků Win32 s ID RT_MANIFEST. Pokud je volána pomocí parametru NULL, všechny dříve přečtené manifesty jsou vymazány. To umožňuje, aby se stav linkeru obnovil na čas inicializace.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje aLink. h  
  
## <a name="see-also"></a>Viz také:

- [IALink3 – rozhraní](ialink3-interface.md)
- [Rozhraní API ALink](index.md)
- [IALink – rozhraní](ialink-interface.md)
- [Al.exe (linker sestavení)](../../tools/al-exe-assembly-linker.md)

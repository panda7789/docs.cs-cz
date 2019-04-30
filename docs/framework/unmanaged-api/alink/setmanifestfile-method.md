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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8307960166cfc668a577431d688c439f0f794be2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949040"
---
# <a name="setmanifestfile-method"></a>SetManifestFile – metoda
Umožňuje zadat nebo obnovit soubor manifestu, který používá propojovací program při vytváření sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFile`  
  
 Název souboru manifestu, jejichž obsah jsou vloženy do objektu blob prostředky Win32.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje, vrátí hodnotu S_OK.  
  
## <a name="remarks"></a>Poznámky  
 Před požadující Win32ResBlob volejte to. Hodnota `pszFile` parametr je název souboru manifestu, jejichž obsah čtou a vložit prostředky Win32 s ID RT_MANIFEST. Při volání s použitím parametr hodnotu NULL, se vymaže všechny dříve čtení manifestu. To umožňuje z nich se má obnovit stav linkeru, inicializuje.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje aLink.h  
  
## <a name="see-also"></a>Viz také:

- [IALink3 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
- [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Al.exe (linker sestavení)](../../../../docs/framework/tools/al-exe-assembly-linker.md)

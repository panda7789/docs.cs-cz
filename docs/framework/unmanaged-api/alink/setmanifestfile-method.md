---
title: "SetManifestFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink3.SetManifestFile
api_location: alink.dll
api_type: COM
f1_keywords: SetManifestFile
helpviewer_keywords: SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 807452326193d193f3bc603ebc7b74a5a0f1c281
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="setmanifestfile-method"></a>SetManifestFile – metoda
Umožňuje zadat nebo obnovit soubor manifestu, který linkeru používá při vytváření sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszFile`  
  
 Název souboru manifestu, jejichž obsah jsou vloženy do objektu blob Win32 prostředky.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="remarks"></a>Poznámky  
 Toto volání před žádostí o Win32ResBlob. Hodnota `pszFile` parametr je název souboru manifestu, jejichž obsah čtou a umístit do Win32 prostředky s ID RT_MANIFEST. Při volání pomocí parametr hodnotu NULL, není zaškrtnuté všechny dříve čtení manifestu. To umožňuje jednu pro obnovení stav linkeru, čas inicializace.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje aLink.h  
  
## <a name="see-also"></a>Viz také  
 [Ialink3 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [Ialink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Al.exe (Linker sestavení)](../../../../docs/framework/tools/al-exe-assembly-linker.md)

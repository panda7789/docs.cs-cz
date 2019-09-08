---
title: ImportTypes2 – metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce09eca30e1edb9e1afc02216a07955a5fed4fd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787253"
---
# <a name="importtypes2-method"></a>ImportTypes2 – metoda
Inicializuje import typů. Zavolejte tuto metodu pro zahájení importu typů z každého oboru importovaného prostřednictvím [metody importFile –](importfile-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení, do kterého se má importovat.  
  
 `FileToken`  
 ID souboru, ze kterého se má importovat.  
  
 `dwScope`  
 Rozsah od nuly, ze kterého se má importovat.  
  
 `phEnum`  
 Přijímá popisovač enumerátoru pro typy v daném oboru.  
  
 `ppImportScope`  
 Volitelně přijímá rozhraní [rozhraní IMetaDataImport2](../metadata/imetadataimport2-interface.md) .  
  
 `pdwCountOfTypes`  
 Volitelně přijímá počet typů v zadaném oboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h  
  
## <a name="see-also"></a>Viz také:

- [IALink2 – rozhraní](ialink2-interface.md)
- [IALink – rozhraní](ialink-interface.md)
- [Rozhraní API ALink](index.md)

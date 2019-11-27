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
ms.openlocfilehash: 8dae903ab76ab83ac0818c4bc4a76e81094bdf65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445661"
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
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h  
  
## <a name="see-also"></a>Viz také:

- [IALink2 – rozhraní](ialink2-interface.md)
- [IALink – rozhraní](ialink-interface.md)
- [Rozhraní API ALink](index.md)

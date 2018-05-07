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
ms.openlocfilehash: 51c696679626a598be422376e9dc89b5add1773d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="importtypes2-method"></a>ImportTypes2 – metoda
Zahájí import typy. Voláním této metody lze importovat z každého oboru importovat prostřednictvím typy [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení, do kterých se má importovat.  
  
 `FileToken`  
 ID souboru ze kterých chcete importovat.  
  
 `dwScope`  
 Počítaný od nuly oboru, ze kterého chcete importovat.  
  
 `phEnum`  
 Získá popisovač výčtu pro typy v daném oboru.  
  
 `ppImportScope`  
 Volitelně obdrží [imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) rozhraní.  
  
 `pdwCountOfTypes`  
 Volitelně přijme počet typů v zadaném oboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h  
  
## <a name="see-also"></a>Viz také  
 [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)

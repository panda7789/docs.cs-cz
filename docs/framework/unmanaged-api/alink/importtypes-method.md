---
title: ImportTypes – metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f19dd114925ed1fd12bcc0056411c3e3d4181215
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777096"
---
# <a name="importtypes-method"></a>ImportTypes – metoda
Inicializuje import typů z každého oboru importovaného pomocí [metody importFile –](importfile-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení, do kterého se má importovat  
  
 `FileToken`  
 ID souboru, ze kterého se má importovat  
  
 `dwScope`  
 Rozsah založený na nule pro import.  
  
 `phEnum`  
 Přijímá popisovač enumerátoru pro typy v tomto oboru.  
  
 `ppImportScope`  
 Volitelně přijímá rozhraní [rozhraní IMetaDataImport](../metadata/imetadataimport-interface.md) .  
  
 `pdwCountOfTypes`  
 Volitelně přijímá počet typů v označeném rozsahu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)

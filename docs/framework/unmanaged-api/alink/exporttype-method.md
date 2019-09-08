---
title: ExportType – metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 455f71c5b576d1b57db591dab2a3e59f8a5eed67
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777282"
---
# <a name="exporttype-method"></a>ExportType – metoda
Určuje, že je možné exportovat typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení, ze kterého se má exportovat  
  
 `FileToken`  
 Token souboru nebo ID sestavení souboru, který definuje exportovatelný typ.  
  
 `TypeToken`  
 Token typu, který se má provést export.  
  
 `pszTypename`  
 Plně kvalifikovaný název typu, který se dá exportovat.  
  
 `dwFlags`  
 `ComType`příznaky jako `tdPublic` nebo `tdNested`. Tento parametr může být předán [metodě DefineExportedType –](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Přijímá token pro exportovaný typ.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)

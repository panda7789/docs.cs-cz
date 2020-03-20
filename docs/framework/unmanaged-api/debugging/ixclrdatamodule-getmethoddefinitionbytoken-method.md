---
title: IXCLRDataModule::Metoda GetMethodDefinitionByToken
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 294c5340caf2217f9337d654a11a63a43d46febd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176666"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a>IXCLRDataModule::Metoda GetMethodDefinitionByToken

Získá definici metody odpovídající daný token metadat.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a>Parametry

`token`\
[v] Token metody.

`methodDefinition`\
[out] Definice metody.

## <a name="remarks"></a>Poznámky

Poskytnutá metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 25.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádný  
**Knihovna:** Žádný  
**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [ladění](index.md)
- [IXCLRDataModule – rozhraní](ixclrdatamodule-interface.md)

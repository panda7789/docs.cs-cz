---
title: CorThreadSafetyOptions – výčet
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d71d2a5b3007d4e877900443af426a9643b29125
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360432"
---
# <a name="corthreadsafetyoptions-enumeration"></a>CorThreadSafetyOptions – výčet

Určuje příznaky a možnosti pro bezpečný přístup z více vláken.

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a>Členové

|Člen|Popis|
|------------|-----------------|
|`MDThreadSafetyDefault`|Výchozí hodnota. Stejné jako `MDThreadSafetyOff`.|
|`MDThreadSafetyOff`|Označuje, že zámek čtení/zápis nelze nastavit.|
|`MDThreadSafetyOn`|Označuje, že můžete nastavit zámek čtení/zápis.|

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** CorHdr.h

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

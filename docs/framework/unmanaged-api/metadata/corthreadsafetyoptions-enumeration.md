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
ms.openlocfilehash: 8c0527a7bc3cde7344bf809dc8e6f5a3fac04852
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007504"
---
# <a name="corthreadsafetyoptions-enumeration"></a>CorThreadSafetyOptions – výčet

Určuje příznaky pro výběr možností pro bezpečnost vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a>Členové

|Člen|Description|
|------------|-----------------|
|`MDThreadSafetyDefault`|Výchozí hodnota. Stejné jako `MDThreadSafetyOff` .|
|`MDThreadSafetyOff`|Indikuje, že zámek čtenář/Writer nejde nastavit.|
|`MDThreadSafetyOn`|Indikuje, že je možné nastavit zámek čtenář/Writer.|

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** CorHdr. h

**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)

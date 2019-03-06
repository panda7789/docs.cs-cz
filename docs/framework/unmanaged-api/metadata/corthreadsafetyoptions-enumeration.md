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
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="d0f01-102">CorThreadSafetyOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="d0f01-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="d0f01-103">Určuje příznaky a možnosti pro bezpečný přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="d0f01-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0f01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0f01-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="d0f01-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d0f01-105">Members</span></span>

|<span data-ttu-id="d0f01-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d0f01-106">Member</span></span>|<span data-ttu-id="d0f01-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d0f01-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="d0f01-108">Výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="d0f01-108">Default value.</span></span> <span data-ttu-id="d0f01-109">Stejné jako `MDThreadSafetyOff`.</span><span class="sxs-lookup"><span data-stu-id="d0f01-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="d0f01-110">Označuje, že zámek čtení/zápis nelze nastavit.</span><span class="sxs-lookup"><span data-stu-id="d0f01-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="d0f01-111">Označuje, že můžete nastavit zámek čtení/zápis.</span><span class="sxs-lookup"><span data-stu-id="d0f01-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="d0f01-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0f01-112">Requirements</span></span>

<span data-ttu-id="d0f01-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0f01-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="d0f01-114">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d0f01-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="d0f01-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0f01-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d0f01-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0f01-116">See also</span></span>

- [<span data-ttu-id="d0f01-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="d0f01-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

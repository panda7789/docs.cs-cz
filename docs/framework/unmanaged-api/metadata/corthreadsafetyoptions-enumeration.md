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
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="04434-102">CorThreadSafetyOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="04434-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="04434-103">Určuje příznaky pro výběr možností pro bezpečnost vlákna.</span><span class="sxs-lookup"><span data-stu-id="04434-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="04434-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04434-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="04434-105">Členové</span><span class="sxs-lookup"><span data-stu-id="04434-105">Members</span></span>

|<span data-ttu-id="04434-106">Člen</span><span class="sxs-lookup"><span data-stu-id="04434-106">Member</span></span>|<span data-ttu-id="04434-107">Description</span><span class="sxs-lookup"><span data-stu-id="04434-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="04434-108">Výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="04434-108">Default value.</span></span> <span data-ttu-id="04434-109">Stejné jako `MDThreadSafetyOff` .</span><span class="sxs-lookup"><span data-stu-id="04434-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="04434-110">Indikuje, že zámek čtenář/Writer nejde nastavit.</span><span class="sxs-lookup"><span data-stu-id="04434-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="04434-111">Indikuje, že je možné nastavit zámek čtenář/Writer.</span><span class="sxs-lookup"><span data-stu-id="04434-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="04434-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04434-112">Requirements</span></span>

<span data-ttu-id="04434-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04434-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="04434-114">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="04434-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="04434-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04434-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="04434-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="04434-116">See also</span></span>

- [<span data-ttu-id="04434-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="04434-117">Metadata Enumerations</span></span>](metadata-enumerations.md)

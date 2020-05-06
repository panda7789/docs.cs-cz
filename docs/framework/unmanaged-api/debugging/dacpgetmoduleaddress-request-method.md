---
title: DacpGetModuleAddress::Request – metoda
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1755526636bed6d78663112e4c2ad5ab7c3f731c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860841"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="05d6e-102">DacpGetModuleAddress::Request – metoda</span><span class="sxs-lookup"><span data-stu-id="05d6e-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="05d6e-103">Provede požadavek na naplnění struktury z dané běhové struktury.</span><span class="sxs-lookup"><span data-stu-id="05d6e-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="05d6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05d6e-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="05d6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05d6e-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="05d6e-106">pro Ukazatel na modul dat o počátečních datech.</span><span class="sxs-lookup"><span data-stu-id="05d6e-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="05d6e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05d6e-107">Remarks</span></span>

<span data-ttu-id="05d6e-108">Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="05d6e-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="05d6e-109">Pokud ho chcete použít, nejjednodušší způsob je napodobení implementace:</span><span class="sxs-lookup"><span data-stu-id="05d6e-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="05d6e-110">Vraťte hodnotu získanou z volání `Request` metody v `IXCLRDataModule*` parametru s následujícími parametry:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="05d6e-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="05d6e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05d6e-111">Requirements</span></span>

<span data-ttu-id="05d6e-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="05d6e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="05d6e-113">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="05d6e-113">**Header:** None\</span></span>
<span data-ttu-id="05d6e-114">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="05d6e-114">**Library:** None\</span></span>
<span data-ttu-id="05d6e-115">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="05d6e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="05d6e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="05d6e-116">See also</span></span>

- [<span data-ttu-id="05d6e-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="05d6e-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="05d6e-118">Struktura DacpGetModuleAddress</span><span class="sxs-lookup"><span data-stu-id="05d6e-118">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)

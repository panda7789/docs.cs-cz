---
title: DacpGetModulAddress::Metoda požadavku
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
ms.openlocfilehash: 4dbe6a2c295e5afae1b6761f0c7b695fdb906428
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102904"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="bceac-102">DacpGetModulAddress::Metoda požadavku</span><span class="sxs-lookup"><span data-stu-id="bceac-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="bceac-103">Provede požadavek na naplnění struktury z dané struktury runtime.</span><span class="sxs-lookup"><span data-stu-id="bceac-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bceac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bceac-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="bceac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bceac-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="bceac-106">[v] Ukazatel na modul dat osiva.</span><span class="sxs-lookup"><span data-stu-id="bceac-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="bceac-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bceac-107">Remarks</span></span>

<span data-ttu-id="bceac-108">Tato struktura žije uvnitř runtime a není vystavena prostřednictvím žádné záhlaví nebo soubory knihovny.</span><span class="sxs-lookup"><span data-stu-id="bceac-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="bceac-109">Chcete-li jej použít, nejjednodušší způsob je napodobit implementaci:</span><span class="sxs-lookup"><span data-stu-id="bceac-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="bceac-110">Vrátí hodnotu získanou voláním `Request` metody parametru `IXCLRDataModule*` s následujícími parametry:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="bceac-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="bceac-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bceac-111">Requirements</span></span>

<span data-ttu-id="bceac-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="bceac-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md)</span></span>\
<span data-ttu-id="bceac-113">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="bceac-113">**Header:** None</span></span>\
<span data-ttu-id="bceac-114">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="bceac-114">**Library:** None</span></span>\
<span data-ttu-id="bceac-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bceac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bceac-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bceac-116">See also</span></span>

- [<span data-ttu-id="bceac-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="bceac-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="bceac-118">DacpGetModuleAddress struktura</span><span class="sxs-lookup"><span data-stu-id="bceac-118">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)

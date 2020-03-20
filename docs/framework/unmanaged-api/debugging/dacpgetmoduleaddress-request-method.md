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
ms.openlocfilehash: 6850dc256a70e0c0343104b3904e9eda62d11e7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179201"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="59f35-102">DacpGetModulAddress::Metoda požadavku</span><span class="sxs-lookup"><span data-stu-id="59f35-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="59f35-103">Provede požadavek na naplnění struktury z dané struktury runtime.</span><span class="sxs-lookup"><span data-stu-id="59f35-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="59f35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59f35-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="59f35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="59f35-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="59f35-106">[v] Ukazatel na modul dat osiva.</span><span class="sxs-lookup"><span data-stu-id="59f35-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="59f35-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59f35-107">Remarks</span></span>

<span data-ttu-id="59f35-108">Tato struktura žije uvnitř runtime a není vystavena prostřednictvím žádné záhlaví nebo soubory knihovny.</span><span class="sxs-lookup"><span data-stu-id="59f35-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="59f35-109">Chcete-li jej použít, nejjednodušší způsob je napodobit implementaci:</span><span class="sxs-lookup"><span data-stu-id="59f35-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="59f35-110">Vrátí hodnotu získanou voláním `Request` metody parametru `IXCLRDataModule*` s následujícími parametry:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="59f35-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="59f35-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59f35-111">Requirements</span></span>

<span data-ttu-id="59f35-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59f35-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="59f35-113">**Záhlaví:** Žádná **knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="59f35-113">**Header:** None **Library:** None</span></span>  
<span data-ttu-id="59f35-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="59f35-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="59f35-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="59f35-115">See also</span></span>

- [<span data-ttu-id="59f35-116">ladění</span><span class="sxs-lookup"><span data-stu-id="59f35-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="59f35-117">DacpGetModuleAddress rozhraní</span><span class="sxs-lookup"><span data-stu-id="59f35-117">DacpGetModuleAddress Interface</span></span>](dacpgetmoduleaddress-structure.md)

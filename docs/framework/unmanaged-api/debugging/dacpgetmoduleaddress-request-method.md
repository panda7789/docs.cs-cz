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
ms.openlocfilehash: 298620092c37b2c02332e9135f73584272e326bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111680"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="7887e-102">DacpGetModuleAddress::Request – metoda</span><span class="sxs-lookup"><span data-stu-id="7887e-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="7887e-103">Provede požadavek na naplnit struktura ze struktury daného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7887e-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7887e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7887e-104">Syntax</span></span>

```
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="7887e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7887e-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="7887e-106">[in] Ukazatel na data modulu počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7887e-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="7887e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7887e-107">Remarks</span></span>

<span data-ttu-id="7887e-108">Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="7887e-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="7887e-109">Jeho použití, je nejjednodušší tak, aby napodoboval implementace:</span><span class="sxs-lookup"><span data-stu-id="7887e-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="7887e-110">Návratová hodnota získaný z volání funkce `Request` metodu `IXCLRDataModule*` parametr s následujícími parametry:</span><span class="sxs-lookup"><span data-stu-id="7887e-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters:</span></span> `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a><span data-ttu-id="7887e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7887e-111">Requirements</span></span>

<span data-ttu-id="7887e-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7887e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7887e-113">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="7887e-113">**Header:** None</span></span>     
<span data-ttu-id="7887e-114">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="7887e-114">**Library:** None</span></span>  
**<span data-ttu-id="7887e-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7887e-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="7887e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7887e-116">See also</span></span>

- [<span data-ttu-id="7887e-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="7887e-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="7887e-118">DacpGetModuleAddress Interface</span><span class="sxs-lookup"><span data-stu-id="7887e-118">DacpGetModuleAddress Interface</span></span>](dacpgetmoduleaddress-structure.md)
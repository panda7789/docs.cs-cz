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
ms.openlocfilehash: 07ad83da2bc608e3c5925664a68eec4a548860e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739226"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="b4349-102">DacpGetModuleAddress::Request – metoda</span><span class="sxs-lookup"><span data-stu-id="b4349-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="b4349-103">Provede požadavek na naplnit struktura ze struktury daného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b4349-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b4349-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4349-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="b4349-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4349-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="b4349-106">[in] Ukazatel na data modulu počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b4349-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4349-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4349-107">Remarks</span></span>

<span data-ttu-id="b4349-108">Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="b4349-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="b4349-109">Jeho použití, je nejjednodušší tak, aby napodoboval implementace:</span><span class="sxs-lookup"><span data-stu-id="b4349-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="b4349-110">Návratová hodnota získaný z volání funkce `Request` metodu `IXCLRDataModule*` parametr s následujícími parametry: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="b4349-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="b4349-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4349-111">Requirements</span></span>

<span data-ttu-id="b4349-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4349-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b4349-113">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="b4349-113">**Header:** None</span></span>     
<span data-ttu-id="b4349-114">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="b4349-114">**Library:** None</span></span>  
<span data-ttu-id="b4349-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b4349-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b4349-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4349-116">See also</span></span>

- [<span data-ttu-id="b4349-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="b4349-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="b4349-118">DacpGetModuleAddress Interface</span><span class="sxs-lookup"><span data-stu-id="b4349-118">DacpGetModuleAddress Interface</span></span>](dacpgetmoduleaddress-structure.md)

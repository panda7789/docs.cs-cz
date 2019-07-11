---
title: IXCLRDataProcess::EnumModule – metoda
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 40ab90a3218d4309cda709004a191e9440fe505d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769584"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="06851-102">IXCLRDataProcess::EnumModule – metoda</span><span class="sxs-lookup"><span data-stu-id="06851-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="06851-103">Vytvoří výčet modulů tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="06851-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="06851-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06851-104">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="06851-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06851-105">Parameters</span></span>

`handle`\
<span data-ttu-id="06851-106">[out v] Popisovač pro vytvoření výčtu moduly.</span><span class="sxs-lookup"><span data-stu-id="06851-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="06851-107">[out] Výčtový modul.</span><span class="sxs-lookup"><span data-stu-id="06851-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="06851-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06851-108">Remarks</span></span>

<span data-ttu-id="06851-109">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 25 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="06851-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="06851-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06851-110">Requirements</span></span>

<span data-ttu-id="06851-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06851-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="06851-112">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="06851-112">**Header:** None</span></span>  
<span data-ttu-id="06851-113">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="06851-113">**Library:** None</span></span>  
<span data-ttu-id="06851-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="06851-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="06851-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06851-115">See also</span></span>

- [<span data-ttu-id="06851-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="06851-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="06851-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="06851-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="06851-118">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="06851-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="06851-119">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="06851-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)

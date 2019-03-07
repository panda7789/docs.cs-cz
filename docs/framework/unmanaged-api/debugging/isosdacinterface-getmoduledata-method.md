---
title: ISOSDacInterface::GetModuleData – metoda
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: ed151f998ed7d28ba7ae170839ce2fa3a1ee6135
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490447"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="bee70-102">ISOSDacInterface::GetModuleData – metoda</span><span class="sxs-lookup"><span data-stu-id="bee70-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="bee70-103">Načte data odpovídající modul načíst na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="bee70-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bee70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bee70-104">Syntax</span></span>

```
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="bee70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bee70-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="bee70-106">[in] Adresa načíst informace pro modul.</span><span class="sxs-lookup"><span data-stu-id="bee70-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="bee70-107">[out] [DacpModuleData struktura](dacpmoduledata-structure.md) k ukládání informací načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="bee70-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>


## <a name="remarks"></a><span data-ttu-id="bee70-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bee70-108">Remarks</span></span>

<span data-ttu-id="bee70-109">Zadaná metoda je součástí `ISOSDacInterface` rozhraní a odpovídá 13 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="bee70-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 13th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="bee70-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bee70-110">Requirements</span></span>

<span data-ttu-id="bee70-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bee70-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="bee70-112">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="bee70-112">**Header:** None</span></span>  
<span data-ttu-id="bee70-113">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="bee70-113">**Library:** None</span></span>  
<span data-ttu-id="bee70-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bee70-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bee70-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bee70-115">See also</span></span>

- [<span data-ttu-id="bee70-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="bee70-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="bee70-117">ISOSDacInterface rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee70-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
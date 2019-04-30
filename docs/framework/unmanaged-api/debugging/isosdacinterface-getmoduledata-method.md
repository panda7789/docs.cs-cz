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
ms.openlocfilehash: 128af261c429228c97d952f1f8d382f46306f711
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922561"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="f3aab-102">ISOSDacInterface::GetModuleData – metoda</span><span class="sxs-lookup"><span data-stu-id="f3aab-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="f3aab-103">Načte data odpovídající modul načíst na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="f3aab-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f3aab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3aab-104">Syntax</span></span>

```
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="f3aab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3aab-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="f3aab-106">[in] Adresa načíst informace pro modul.</span><span class="sxs-lookup"><span data-stu-id="f3aab-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="f3aab-107">[out] [DacpModuleData struktura](dacpmoduledata-structure.md) k ukládání informací načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="f3aab-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="f3aab-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3aab-108">Remarks</span></span>

<span data-ttu-id="f3aab-109">Zadaná metoda je součástí `ISOSDacInterface` rozhraní a odpovídá 13 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="f3aab-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 13th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f3aab-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3aab-110">Requirements</span></span>

<span data-ttu-id="f3aab-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3aab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f3aab-112">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="f3aab-112">**Header:** None</span></span>  
<span data-ttu-id="f3aab-113">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="f3aab-113">**Library:** None</span></span>  
<span data-ttu-id="f3aab-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f3aab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f3aab-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3aab-115">See also</span></span>

- [<span data-ttu-id="f3aab-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="f3aab-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="f3aab-117">ISOSDacInterface rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3aab-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
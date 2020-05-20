---
title: 'IXCLRDataProcess:: EnumModule – metoda'
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
ms.openlocfilehash: 5caadcfe091393a8ff79106d57a50a532c349829
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420770"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="236f1-102">IXCLRDataProcess:: EnumModule – metoda</span><span class="sxs-lookup"><span data-stu-id="236f1-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="236f1-103">Vytvoří výčet modulů tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="236f1-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="236f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="236f1-104">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="236f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="236f1-105">Parameters</span></span>

`handle`\
<span data-ttu-id="236f1-106">[in, out] Popisovač pro vytváření výčtu modulů.</span><span class="sxs-lookup"><span data-stu-id="236f1-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="236f1-107">mimo Výčtový modul.</span><span class="sxs-lookup"><span data-stu-id="236f1-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="236f1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="236f1-108">Remarks</span></span>

<span data-ttu-id="236f1-109">Poskytnutá metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 25 slotu tabulky virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="236f1-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="236f1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="236f1-110">Requirements</span></span>

<span data-ttu-id="236f1-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="236f1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="236f1-112">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="236f1-112">**Header:** None</span></span>  
<span data-ttu-id="236f1-113">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="236f1-113">**Library:** None</span></span>  
<span data-ttu-id="236f1-114">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="236f1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="236f1-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="236f1-115">See also</span></span>

- [<span data-ttu-id="236f1-116">Výčet CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="236f1-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="236f1-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="236f1-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="236f1-118">IXCLRDataModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="236f1-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="236f1-119">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="236f1-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)

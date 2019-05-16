---
title: IXCLRDataModule::GetVersionId – metoda
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 6ec18bcf079c7687df4ac9b7c5db23b84383c517
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632299"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="ff501-102">IXCLRDataModule::GetVersionId – metoda</span><span class="sxs-lookup"><span data-stu-id="ff501-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="ff501-103">Získá identifikátor verze modulu.</span><span class="sxs-lookup"><span data-stu-id="ff501-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ff501-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff501-104">Syntax</span></span>

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="ff501-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff501-105">Parameters</span></span>

`vid`\
<span data-ttu-id="ff501-106">[out] Identifikátor verze modulu.</span><span class="sxs-lookup"><span data-stu-id="ff501-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff501-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff501-107">Remarks</span></span>

<span data-ttu-id="ff501-108">Zadaná metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 40 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="ff501-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff501-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff501-109">Requirements</span></span>

<span data-ttu-id="ff501-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff501-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ff501-111">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="ff501-111">**Header:** None</span></span>  
<span data-ttu-id="ff501-112">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="ff501-112">**Library:** None</span></span>  
<span data-ttu-id="ff501-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ff501-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ff501-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff501-114">See also</span></span>

- [<span data-ttu-id="ff501-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="ff501-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="ff501-116">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="ff501-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)

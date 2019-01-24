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
ms.openlocfilehash: 5184db00b10b53011f24c5096b470608e84546b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567422"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="749c0-102">IXCLRDataModule::GetVersionId – metoda</span><span class="sxs-lookup"><span data-stu-id="749c0-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="749c0-103">Získá identifikátor verze modulu.</span><span class="sxs-lookup"><span data-stu-id="749c0-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="749c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="749c0-104">Syntax</span></span>

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

### <a name="parameters"></a><span data-ttu-id="749c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="749c0-105">Parameters</span></span>

<span data-ttu-id="749c0-106">`vid` [out] Identifikátor verze modulu.</span><span class="sxs-lookup"><span data-stu-id="749c0-106">`vid` [out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="749c0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="749c0-107">Remarks</span></span>

<span data-ttu-id="749c0-108">Zadaná metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 40 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="749c0-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="749c0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="749c0-109">Requirements</span></span>

<span data-ttu-id="749c0-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="749c0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="749c0-111">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="749c0-111">**Header:** None</span></span>  
<span data-ttu-id="749c0-112">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="749c0-112">**Library:** None</span></span>  
<span data-ttu-id="749c0-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="749c0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="749c0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="749c0-114">See also</span></span>

- [<span data-ttu-id="749c0-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="749c0-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="749c0-116">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="749c0-116">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)

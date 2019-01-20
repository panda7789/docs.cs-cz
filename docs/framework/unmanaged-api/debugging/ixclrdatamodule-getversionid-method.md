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
ms.openlocfilehash: ac4111abdf6a471aca1eca72a86e33698debbff6
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416077"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="f754e-102">IXCLRDataModule::GetVersionId – metoda</span><span class="sxs-lookup"><span data-stu-id="f754e-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="f754e-103">Získá identifikátor verze modulu.</span><span class="sxs-lookup"><span data-stu-id="f754e-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f754e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f754e-104">Syntax</span></span>

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

### <a name="parameters"></a><span data-ttu-id="f754e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f754e-105">Parameters</span></span>

<span data-ttu-id="f754e-106">`vid` [out] Identifikátor verze modulu.</span><span class="sxs-lookup"><span data-stu-id="f754e-106">`vid` [out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="f754e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f754e-107">Remarks</span></span>

<span data-ttu-id="f754e-108">Zadaná metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 40 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="f754e-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f754e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f754e-109">Requirements</span></span>

<span data-ttu-id="f754e-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f754e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f754e-111">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="f754e-111">**Header:** None</span></span>  
<span data-ttu-id="f754e-112">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="f754e-112">**Library:** None</span></span>  
<span data-ttu-id="f754e-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f754e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f754e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f754e-114">See Also</span></span>

- [<span data-ttu-id="f754e-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="f754e-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="f754e-116">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="f754e-116">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)

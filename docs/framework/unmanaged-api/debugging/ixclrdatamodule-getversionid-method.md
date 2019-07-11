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
ms.openlocfilehash: 5bd84f784ea92e7b2ce2465e64972dc84e16a16c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744703"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="f4e51-102">IXCLRDataModule::GetVersionId – metoda</span><span class="sxs-lookup"><span data-stu-id="f4e51-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="f4e51-103">Získá identifikátor verze modulu.</span><span class="sxs-lookup"><span data-stu-id="f4e51-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f4e51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4e51-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="f4e51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4e51-105">Parameters</span></span>

`vid`\
<span data-ttu-id="f4e51-106">[out] Identifikátor verze modulu.</span><span class="sxs-lookup"><span data-stu-id="f4e51-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4e51-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4e51-107">Remarks</span></span>

<span data-ttu-id="f4e51-108">Zadaná metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 40 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="f4e51-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f4e51-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4e51-109">Requirements</span></span>

<span data-ttu-id="f4e51-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4e51-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f4e51-111">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="f4e51-111">**Header:** None</span></span>  
<span data-ttu-id="f4e51-112">**Knihovna:** Žádný</span><span class="sxs-lookup"><span data-stu-id="f4e51-112">**Library:** None</span></span>  
<span data-ttu-id="f4e51-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f4e51-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f4e51-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4e51-114">See also</span></span>

- [<span data-ttu-id="f4e51-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="f4e51-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="f4e51-116">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="f4e51-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)

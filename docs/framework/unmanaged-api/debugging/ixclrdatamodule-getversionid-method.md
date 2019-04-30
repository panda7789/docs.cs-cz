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
ms.openlocfilehash: e863f14676acc84f4d9f59d0898dee5b291bd30f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775437"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="db763-102">IXCLRDataModule::GetVersionId – metoda</span><span class="sxs-lookup"><span data-stu-id="db763-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="db763-103">Získá identifikátor verze modulu.</span><span class="sxs-lookup"><span data-stu-id="db763-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="db763-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db763-104">Syntax</span></span>

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="db763-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db763-105">Parameters</span></span>

`vid`\
<span data-ttu-id="db763-106">[out] Identifikátor verze modulu.</span><span class="sxs-lookup"><span data-stu-id="db763-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="db763-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db763-107">Remarks</span></span>

<span data-ttu-id="db763-108">Zadaná metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 40 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="db763-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="db763-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db763-109">Requirements</span></span>

<span data-ttu-id="db763-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db763-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="db763-111">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="db763-111">**Header:** None</span></span>  
<span data-ttu-id="db763-112">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="db763-112">**Library:** None</span></span>  
<span data-ttu-id="db763-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="db763-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="db763-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db763-114">See also</span></span>

- [<span data-ttu-id="db763-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="db763-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="db763-116">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="db763-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
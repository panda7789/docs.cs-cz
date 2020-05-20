---
title: 'IXCLRDataModule:: GetVersionId – metoda'
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
ms.openlocfilehash: 9d5ef137a5d76c3d7545ab16921352123e978fb1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420861"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="e9699-102">IXCLRDataModule:: GetVersionId – metoda</span><span class="sxs-lookup"><span data-stu-id="e9699-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="e9699-103">Získá identifikátor verze modulu.</span><span class="sxs-lookup"><span data-stu-id="e9699-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e9699-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9699-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="e9699-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9699-105">Parameters</span></span>

`vid`\
<span data-ttu-id="e9699-106">mimo Identifikátor verze modulu</span><span class="sxs-lookup"><span data-stu-id="e9699-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9699-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9699-107">Remarks</span></span>

<span data-ttu-id="e9699-108">Poskytnutá metoda je součástí `IXCLRDataModule` rozhraní a odpovídá slotu 41st tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="e9699-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e9699-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9699-109">Requirements</span></span>

<span data-ttu-id="e9699-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9699-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e9699-111">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="e9699-111">**Header:** None</span></span>  
<span data-ttu-id="e9699-112">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="e9699-112">**Library:** None</span></span>  
<span data-ttu-id="e9699-113">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e9699-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e9699-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9699-114">See also</span></span>

- [<span data-ttu-id="e9699-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="e9699-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="e9699-116">IXCLRDataModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9699-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)

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
ms.openlocfilehash: ff8ccf42d1131fb15d7473ae12ecefde9d55177f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395282"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="431d5-102">IXCLRDataModule:: GetVersionId – metoda</span><span class="sxs-lookup"><span data-stu-id="431d5-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="431d5-103">Získá identifikátor verze modulu.</span><span class="sxs-lookup"><span data-stu-id="431d5-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="431d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="431d5-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="431d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="431d5-105">Parameters</span></span>

`vid`\
<span data-ttu-id="431d5-106">mimo Identifikátor verze modulu</span><span class="sxs-lookup"><span data-stu-id="431d5-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="431d5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="431d5-107">Remarks</span></span>

<span data-ttu-id="431d5-108">Poskytnutá metoda je součástí `IXCLRDataModule` rozhraní a odpovídá slotu 41st tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="431d5-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="431d5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="431d5-109">Requirements</span></span>

<span data-ttu-id="431d5-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="431d5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="431d5-111">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="431d5-111">**Header:** None</span></span>  
<span data-ttu-id="431d5-112">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="431d5-112">**Library:** None</span></span>  
<span data-ttu-id="431d5-113">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="431d5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="431d5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="431d5-114">See also</span></span>

- [<span data-ttu-id="431d5-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="431d5-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="431d5-116">IXCLRDataModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="431d5-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)

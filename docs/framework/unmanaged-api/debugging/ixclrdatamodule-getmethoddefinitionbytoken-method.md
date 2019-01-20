---
title: IXCLRDataModule::GetMethodDefinitionByToken – metoda
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 27f1ee28aff95340d4b533473b2f699a9405c3a2
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416124"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="dcd36-102">IXCLRDataModule::GetMethodDefinitionByToken – metoda</span><span class="sxs-lookup"><span data-stu-id="dcd36-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="dcd36-103">Získá definici metody odpovídající token daná metadata.</span><span class="sxs-lookup"><span data-stu-id="dcd36-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="dcd36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcd36-104">Syntax</span></span>

```
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

### <a name="parameters"></a><span data-ttu-id="dcd36-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcd36-105">Parameters</span></span>

<span data-ttu-id="dcd36-106">`token` [in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="dcd36-106">`token` [in] The method token.</span></span>

<span data-ttu-id="dcd36-107">`methodDefinition` [out] Definice metody.</span><span class="sxs-lookup"><span data-stu-id="dcd36-107">`methodDefinition` [out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="dcd36-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcd36-108">Remarks</span></span>

<span data-ttu-id="dcd36-109">Zadaná metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 25 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="dcd36-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="dcd36-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcd36-110">Requirements</span></span>

<span data-ttu-id="dcd36-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcd36-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="dcd36-112">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="dcd36-112">**Header:** None</span></span>  
<span data-ttu-id="dcd36-113">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="dcd36-113">**Library:** None</span></span>  
<span data-ttu-id="dcd36-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dcd36-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="dcd36-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcd36-115">See Also</span></span>

- [<span data-ttu-id="dcd36-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="dcd36-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="dcd36-117">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="dcd36-117">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)

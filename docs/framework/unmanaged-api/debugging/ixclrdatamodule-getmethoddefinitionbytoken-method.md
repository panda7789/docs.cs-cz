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
ms.openlocfilehash: 1371b86f30324908a639b3b1bbae0ae007ba590a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708087"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="bb1eb-102">IXCLRDataModule::GetMethodDefinitionByToken – metoda</span><span class="sxs-lookup"><span data-stu-id="bb1eb-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="bb1eb-103">Získá definici metody odpovídající token daná metadata.</span><span class="sxs-lookup"><span data-stu-id="bb1eb-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bb1eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb1eb-104">Syntax</span></span>

```
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

### <a name="parameters"></a><span data-ttu-id="bb1eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb1eb-105">Parameters</span></span>

<span data-ttu-id="bb1eb-106">`token` [in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="bb1eb-106">`token` [in] The method token.</span></span>

<span data-ttu-id="bb1eb-107">`methodDefinition` [out] Definice metody.</span><span class="sxs-lookup"><span data-stu-id="bb1eb-107">`methodDefinition` [out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb1eb-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb1eb-108">Remarks</span></span>

<span data-ttu-id="bb1eb-109">Zadaná metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 25 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="bb1eb-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb1eb-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb1eb-110">Requirements</span></span>

<span data-ttu-id="bb1eb-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb1eb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="bb1eb-112">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="bb1eb-112">**Header:** None</span></span>  
<span data-ttu-id="bb1eb-113">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="bb1eb-113">**Library:** None</span></span>  
<span data-ttu-id="bb1eb-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bb1eb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="bb1eb-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb1eb-115">See also</span></span>

- [<span data-ttu-id="bb1eb-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="bb1eb-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="bb1eb-117">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="bb1eb-117">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)

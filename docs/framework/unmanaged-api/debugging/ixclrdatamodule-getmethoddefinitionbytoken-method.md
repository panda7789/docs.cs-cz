---
title: IXCLRDataModule::Metoda GetMethodDefinitionByToken
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
ms.openlocfilehash: 294c5340caf2217f9337d654a11a63a43d46febd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176666"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="eb5bf-102">IXCLRDataModule::Metoda GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="eb5bf-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="eb5bf-103">Získá definici metody odpovídající daný token metadat.</span><span class="sxs-lookup"><span data-stu-id="eb5bf-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="eb5bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb5bf-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="eb5bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb5bf-105">Parameters</span></span>

`token`\
<span data-ttu-id="eb5bf-106">[v] Token metody.</span><span class="sxs-lookup"><span data-stu-id="eb5bf-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="eb5bf-107">[out] Definice metody.</span><span class="sxs-lookup"><span data-stu-id="eb5bf-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb5bf-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb5bf-108">Remarks</span></span>

<span data-ttu-id="eb5bf-109">Poskytnutá metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 25.</span><span class="sxs-lookup"><span data-stu-id="eb5bf-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb5bf-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb5bf-110">Requirements</span></span>

<span data-ttu-id="eb5bf-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb5bf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="eb5bf-112">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="eb5bf-112">**Header:** None</span></span>  
<span data-ttu-id="eb5bf-113">**Knihovna:** Žádný</span><span class="sxs-lookup"><span data-stu-id="eb5bf-113">**Library:** None</span></span>  
<span data-ttu-id="eb5bf-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eb5bf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="eb5bf-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb5bf-115">See also</span></span>

- [<span data-ttu-id="eb5bf-116">ladění</span><span class="sxs-lookup"><span data-stu-id="eb5bf-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="eb5bf-117">IXCLRDataModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb5bf-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)

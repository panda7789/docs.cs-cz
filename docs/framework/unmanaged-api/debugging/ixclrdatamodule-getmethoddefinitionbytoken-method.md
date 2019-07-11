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
ms.openlocfilehash: 2c0cf56f108396226b7c7399f6da75e5f47d36f3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744667"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="2fc86-102">IXCLRDataModule::GetMethodDefinitionByToken – metoda</span><span class="sxs-lookup"><span data-stu-id="2fc86-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="2fc86-103">Získá definici metody odpovídající token daná metadata.</span><span class="sxs-lookup"><span data-stu-id="2fc86-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2fc86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fc86-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="2fc86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fc86-105">Parameters</span></span>

`token`\
<span data-ttu-id="2fc86-106">[in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="2fc86-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="2fc86-107">[out] Definice metody.</span><span class="sxs-lookup"><span data-stu-id="2fc86-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fc86-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fc86-108">Remarks</span></span>

<span data-ttu-id="2fc86-109">Zadaná metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 25 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="2fc86-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2fc86-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2fc86-110">Requirements</span></span>

<span data-ttu-id="2fc86-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fc86-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2fc86-112">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="2fc86-112">**Header:** None</span></span>  
<span data-ttu-id="2fc86-113">**Knihovna:** Žádný</span><span class="sxs-lookup"><span data-stu-id="2fc86-113">**Library:** None</span></span>  
<span data-ttu-id="2fc86-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2fc86-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="2fc86-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fc86-115">See also</span></span>

- [<span data-ttu-id="2fc86-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="2fc86-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="2fc86-117">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="2fc86-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)

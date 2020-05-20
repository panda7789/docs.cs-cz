---
title: 'IXCLRDataModule:: GetMethodDefinitionByToken – metoda'
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
ms.openlocfilehash: 074949145be588fc34266a9f2ee501caeeffb9d3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420874"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="8d6fa-102">IXCLRDataModule:: GetMethodDefinitionByToken – metoda</span><span class="sxs-lookup"><span data-stu-id="8d6fa-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="8d6fa-103">Získá definici metody odpovídající danému tokenu metadat.</span><span class="sxs-lookup"><span data-stu-id="8d6fa-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="8d6fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d6fa-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="8d6fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d6fa-105">Parameters</span></span>

`token`\
<span data-ttu-id="8d6fa-106">pro Token metody.</span><span class="sxs-lookup"><span data-stu-id="8d6fa-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="8d6fa-107">mimo Definice metody.</span><span class="sxs-lookup"><span data-stu-id="8d6fa-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d6fa-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d6fa-108">Remarks</span></span>

<span data-ttu-id="8d6fa-109">Poskytnutá metoda je součástí `IXCLRDataModule` rozhraní a odpovídá slotu 26 tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="8d6fa-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="8d6fa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d6fa-110">Requirements</span></span>

<span data-ttu-id="8d6fa-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d6fa-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="8d6fa-112">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="8d6fa-112">**Header:** None</span></span>  
<span data-ttu-id="8d6fa-113">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="8d6fa-113">**Library:** None</span></span>  
<span data-ttu-id="8d6fa-114">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8d6fa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="8d6fa-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d6fa-115">See also</span></span>

- [<span data-ttu-id="8d6fa-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="8d6fa-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="8d6fa-117">IXCLRDataModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d6fa-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)

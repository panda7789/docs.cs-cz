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
ms.openlocfilehash: c70920205b27376d453bdd0a13223c6a5569075b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395300"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="d1bfb-102">IXCLRDataModule:: GetMethodDefinitionByToken – metoda</span><span class="sxs-lookup"><span data-stu-id="d1bfb-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="d1bfb-103">Získá definici metody odpovídající danému tokenu metadat.</span><span class="sxs-lookup"><span data-stu-id="d1bfb-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d1bfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1bfb-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="d1bfb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1bfb-105">Parameters</span></span>

`token`\
<span data-ttu-id="d1bfb-106">pro Token metody.</span><span class="sxs-lookup"><span data-stu-id="d1bfb-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="d1bfb-107">mimo Definice metody.</span><span class="sxs-lookup"><span data-stu-id="d1bfb-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1bfb-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1bfb-108">Remarks</span></span>

<span data-ttu-id="d1bfb-109">Poskytnutá metoda je součástí `IXCLRDataModule` rozhraní a odpovídá slotu 26 tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="d1bfb-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d1bfb-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1bfb-110">Requirements</span></span>

<span data-ttu-id="d1bfb-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1bfb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d1bfb-112">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="d1bfb-112">**Header:** None</span></span>  
<span data-ttu-id="d1bfb-113">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="d1bfb-113">**Library:** None</span></span>  
<span data-ttu-id="d1bfb-114">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d1bfb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d1bfb-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1bfb-115">See also</span></span>

- [<span data-ttu-id="d1bfb-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="d1bfb-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="d1bfb-117">IXCLRDataModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1bfb-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)

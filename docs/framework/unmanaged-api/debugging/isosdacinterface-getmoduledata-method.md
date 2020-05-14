---
title: 'ISOSDacInterface:: GetModuleData – metoda'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 14e0eb812c84a0042150345d039451adf178caf1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396914"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="99817-102">ISOSDacInterface:: GetModuleData – metoda</span><span class="sxs-lookup"><span data-stu-id="99817-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="99817-103">Načte data odpovídající modulu načtenému na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="99817-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="99817-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99817-104">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="99817-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99817-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="99817-106">pro Adresa modulu, pro který mají být načteny informace.</span><span class="sxs-lookup"><span data-stu-id="99817-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="99817-107">mimo [Struktura DacpModuleData](dacpmoduledata-structure.md) pro uchovávání informací načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="99817-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="99817-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99817-108">Remarks</span></span>

<span data-ttu-id="99817-109">Poskytnutá metoda je součástí `ISOSDacInterface` rozhraní a odpovídá slotu 14 tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="99817-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="99817-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99817-110">Requirements</span></span>

<span data-ttu-id="99817-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99817-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="99817-112">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="99817-112">**Header:** None</span></span>  
<span data-ttu-id="99817-113">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="99817-113">**Library:** None</span></span>  
<span data-ttu-id="99817-114">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="99817-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="99817-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="99817-115">See also</span></span>

- [<span data-ttu-id="99817-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="99817-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="99817-117">ISOSDacInterface – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99817-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)

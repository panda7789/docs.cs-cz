---
title: ISOSDacInterface – rozhraní
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c9b4e6e5b36fe38b6c0ea78f6d1848d155008bcc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420965"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="04640-102">ISOSDacInterface – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04640-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="04640-103">Poskytuje pomocné metody pro přístup k datům z `SOS` .</span><span class="sxs-lookup"><span data-stu-id="04640-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="04640-104">Metody</span><span class="sxs-lookup"><span data-stu-id="04640-104">Methods</span></span>

| <span data-ttu-id="04640-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="04640-105">Method</span></span>                                                                                                               | <span data-ttu-id="04640-106">Popis</span><span class="sxs-lookup"><span data-stu-id="04640-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="04640-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="04640-107">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="04640-108">Načte data pro daný ukazatel MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="04640-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="04640-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="04640-109">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="04640-110">Načte ukazatel MethodDesc odpovídající metodě, která obsahuje danou adresu nativní instrukce.</span><span class="sxs-lookup"><span data-stu-id="04640-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="04640-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="04640-111">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="04640-112">Načte data odpovídající modulu načtenému na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="04640-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="04640-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04640-113">Remarks</span></span>

<span data-ttu-id="04640-114">Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="04640-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="04640-115">Jedná se však o rozhraní modelu COM, které je odvozeno z `IUnknown` identifikátoru GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` , který lze získat prostřednictvím obvyklých mechanismů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="04640-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="04640-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04640-116">Requirements</span></span>

<span data-ttu-id="04640-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04640-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="04640-118">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="04640-118">**Header:** None</span></span>  
<span data-ttu-id="04640-119">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="04640-119">**Library:** None</span></span>  
<span data-ttu-id="04640-120">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="04640-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="04640-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="04640-121">See also</span></span>

- [<span data-ttu-id="04640-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="04640-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="04640-123">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04640-123">Debugging Interfaces</span></span>](debugging-interfaces.md)

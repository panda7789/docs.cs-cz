---
title: ICorDebugProcess4 – rozhraní
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: fcf725ea98fa4351e72cf592f92968ee2233ecb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213579"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="611a1-102">ICorDebugProcess4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="611a1-102">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="611a1-103">Poskytuje podporu pro vzdálené řízení spouštění procesů.</span><span class="sxs-lookup"><span data-stu-id="611a1-103">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="611a1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="611a1-104">Methods</span></span>

| <span data-ttu-id="611a1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="611a1-105">Method</span></span>                                                                 | <span data-ttu-id="611a1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="611a1-106">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="611a1-107">ProcessStateChanged –</span><span class="sxs-lookup"><span data-stu-id="611a1-107">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="611a1-108">Upozorní kanál ICorDebug, že proces ladicího programu mimo proces pokračuje v provádění laděného objektu.</span><span class="sxs-lookup"><span data-stu-id="611a1-108">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="611a1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="611a1-109">Remarks</span></span>

<span data-ttu-id="611a1-110">Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="611a1-110">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="611a1-111">Jedná se však o rozhraní modelu COM, které je odvozeno z `IUnknown` identifikátoru GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` , který lze získat prostřednictvím obvyklých mechanismů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="611a1-111">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="611a1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="611a1-112">Requirements</span></span>

<span data-ttu-id="611a1-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="611a1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="611a1-114">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="611a1-114">**Header:** None</span></span>

<span data-ttu-id="611a1-115">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="611a1-115">**Library:** None</span></span>

<span data-ttu-id="611a1-116">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="611a1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="611a1-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="611a1-117">See also</span></span>

- [<span data-ttu-id="611a1-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="611a1-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="611a1-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="611a1-119">Debugging</span></span>](index.md)

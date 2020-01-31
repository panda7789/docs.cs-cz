---
title: ICorProfilerInfo9 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 371e85ce8f5d7b420a30ac842ec658949e47d30e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861642"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="bd353-102">ICorProfilerInfo9 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd353-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="bd353-103">Podtřída [ICorProfilerInfo8](icorprofilerinfo8-interface.md) , která poskytuje metody pro dotazování na informace o funkcích s více nativními verzemi kódu.</span><span class="sxs-lookup"><span data-stu-id="bd353-103">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="bd353-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bd353-104">Methods</span></span>  

| <span data-ttu-id="bd353-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bd353-105">Method</span></span>|<span data-ttu-id="bd353-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bd353-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="bd353-107">Metoda GetNativeCodeStartAddresses</span><span class="sxs-lookup"><span data-stu-id="bd353-107">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="bd353-108">S ohledem na functionId a rejitId vytvoří výčet počáteční adresy kódu pro všechny zpracovaných kompilátorem JIT verze tohoto kódu, který aktuálně existuje.</span><span class="sxs-lookup"><span data-stu-id="bd353-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="bd353-109">Metoda GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="bd353-109">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="bd353-110">Vzhledem k počáteční adrese nativního kódu vrací nativní informace mapování IL pro tuto verzi zpracovaných kompilátorem JIT kódu.</span><span class="sxs-lookup"><span data-stu-id="bd353-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="bd353-111">Metoda GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="bd353-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="bd353-112">Vzhledem k počáteční adrese nativního kódu vrátí bloky virtuální paměti, která ukládá tento kód.</span><span class="sxs-lookup"><span data-stu-id="bd353-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="bd353-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd353-113">Requirements</span></span>  
<span data-ttu-id="bd353-114">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="bd353-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="bd353-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bd353-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="bd353-116">**Verze rozhraní .NET:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd353-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bd353-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd353-117">See also</span></span>

- [<span data-ttu-id="bd353-118">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="bd353-118">Profiling Interfaces</span></span>](profiling-interfaces.md)

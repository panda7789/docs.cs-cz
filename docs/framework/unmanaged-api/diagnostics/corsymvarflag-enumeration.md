---
title: CorSymVarFlag – výčet
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5b387ee7fd4cc0088c90d2b8278fbf18bb36f51
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755683"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="e17a0-102">CorSymVarFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="e17a0-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="e17a0-103">Označuje, zda proměnná je generovaný kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="e17a0-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e17a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e17a0-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="e17a0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e17a0-105">Members</span></span>  
  
|<span data-ttu-id="e17a0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e17a0-106">Member</span></span>|<span data-ttu-id="e17a0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e17a0-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="e17a0-108">Označuje, že danou proměnnou je generovaný kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="e17a0-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e17a0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e17a0-109">Requirements</span></span>  
 <span data-ttu-id="e17a0-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e17a0-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e17a0-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e17a0-111">See also</span></span>

- [<span data-ttu-id="e17a0-112">Výčty pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="e17a0-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)

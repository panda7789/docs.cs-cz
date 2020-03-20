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
ms.openlocfilehash: 21e92d8f2fb80c4c41d516ef281bf4fc8a75f4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176640"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="2073d-102">CorSymVarFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="2073d-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="2073d-103">Označuje, zda je generována proměnná kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2073d-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2073d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2073d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="2073d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2073d-105">Members</span></span>  
  
|<span data-ttu-id="2073d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2073d-106">Member</span></span>|<span data-ttu-id="2073d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2073d-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="2073d-108">Označuje, že daná proměnná je generována kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="2073d-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2073d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2073d-109">Requirements</span></span>  
 <span data-ttu-id="2073d-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2073d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2073d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="2073d-111">See also</span></span>

- [<span data-ttu-id="2073d-112">Výčty úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="2073d-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)

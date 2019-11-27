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
ms.openlocfilehash: 86cac53508665c3c97caaa415d8d3c38660928bb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448559"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="8bf49-102">CorSymVarFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="8bf49-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="8bf49-103">Označuje, zda je proměnná vygenerována kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="8bf49-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bf49-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="8bf49-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8bf49-105">Members</span></span>  
  
|<span data-ttu-id="8bf49-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8bf49-106">Member</span></span>|<span data-ttu-id="8bf49-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8bf49-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="8bf49-108">Označuje, že daná proměnná je vygenerovaná kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="8bf49-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8bf49-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8bf49-109">Requirements</span></span>  
 <span data-ttu-id="8bf49-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8bf49-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf49-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bf49-111">See also</span></span>

- [<span data-ttu-id="8bf49-112">Výčty pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="8bf49-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)

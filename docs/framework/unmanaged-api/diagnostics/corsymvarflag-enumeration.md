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
ms.openlocfilehash: d41e048b67d4bc7159f6dd5266457651f1658290
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420588"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="d7c53-102">CorSymVarFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="d7c53-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="d7c53-103">Označuje, zda je proměnná vygenerována kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="d7c53-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7c53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7c53-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="d7c53-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d7c53-105">Members</span></span>  
  
|<span data-ttu-id="d7c53-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d7c53-106">Member</span></span>|<span data-ttu-id="d7c53-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d7c53-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="d7c53-108">Označuje, že daná proměnná je vygenerovaná kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="d7c53-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7c53-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7c53-109">Requirements</span></span>  
 <span data-ttu-id="d7c53-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d7c53-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c53-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7c53-111">See also</span></span>

- [<span data-ttu-id="d7c53-112">Výčty úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="d7c53-112">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)

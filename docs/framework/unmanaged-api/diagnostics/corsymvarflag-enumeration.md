---
title: "CorSymVarFlag – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymVarFlag
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymVarFlag
helpviewer_keywords: CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: edbbc8109eb44494c7f4fac0ed8756e23bdc955b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="de86e-102">CorSymVarFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="de86e-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="de86e-103">Určuje, zda je proměnná generované kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="de86e-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de86e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de86e-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="de86e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="de86e-105">Members</span></span>  
  
|<span data-ttu-id="de86e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="de86e-106">Member</span></span>|<span data-ttu-id="de86e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="de86e-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="de86e-108">Označuje, že daný proměnné je generované kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="de86e-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="de86e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de86e-109">Requirements</span></span>  
 <span data-ttu-id="de86e-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="de86e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de86e-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="de86e-111">See Also</span></span>  
 [<span data-ttu-id="de86e-112">Výčty úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="de86e-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)

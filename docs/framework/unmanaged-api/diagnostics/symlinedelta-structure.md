---
title: "SYMLINEDELTA – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: SYMLINEDELTA
api_location: diasymreader.dll
api_type: COM
f1_keywords: SYMLINEDELTA
helpviewer_keywords: SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cbd83560516e946c03a0ea71cf79fe6d3396bacb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="e29c1-102">SYMLINEDELTA – struktura</span><span class="sxs-lookup"><span data-stu-id="e29c1-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="e29c1-103">Obsahuje informace, které obslužná rutina symbol o metodách, které byly přesunuty v důsledku úpravy.</span><span class="sxs-lookup"><span data-stu-id="e29c1-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e29c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e29c1-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="e29c1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e29c1-105">Members</span></span>  
  
|<span data-ttu-id="e29c1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e29c1-106">Member</span></span>|<span data-ttu-id="e29c1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e29c1-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="e29c1-108">Pro metodu token metadat.</span><span class="sxs-lookup"><span data-stu-id="e29c1-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="e29c1-109">Počet řádků, který byl přesunut metodu.</span><span class="sxs-lookup"><span data-stu-id="e29c1-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e29c1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e29c1-110">Requirements</span></span>  
 <span data-ttu-id="e29c1-111">**Záhlaví:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="e29c1-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e29c1-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e29c1-112">See Also</span></span>  
 [<span data-ttu-id="e29c1-113">Struktury úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="e29c1-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)

---
title: SYMLINEDELTA – struktura
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77cd8b7d791d11f6d40386f4747c60cd4832521a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428091"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="1de20-102">SYMLINEDELTA – struktura</span><span class="sxs-lookup"><span data-stu-id="1de20-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="1de20-103">Obsahuje informace, které obslužná rutina symbol o metodách, které byly přesunuty v důsledku úpravy.</span><span class="sxs-lookup"><span data-stu-id="1de20-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1de20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1de20-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="1de20-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1de20-105">Members</span></span>  
  
|<span data-ttu-id="1de20-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1de20-106">Member</span></span>|<span data-ttu-id="1de20-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1de20-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="1de20-108">Pro metodu token metadat.</span><span class="sxs-lookup"><span data-stu-id="1de20-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="1de20-109">Počet řádků, který byl přesunut metodu.</span><span class="sxs-lookup"><span data-stu-id="1de20-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1de20-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1de20-110">Requirements</span></span>  
 <span data-ttu-id="1de20-111">**Záhlaví:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="1de20-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1de20-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="1de20-112">See Also</span></span>  
 [<span data-ttu-id="1de20-113">Struktury pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="1de20-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)

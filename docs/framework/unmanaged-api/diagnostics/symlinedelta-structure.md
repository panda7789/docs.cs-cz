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
ms.openlocfilehash: fabc8f77b12865d0d971b5934d7de27b52f3e813
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159481"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="4df08-102">SYMLINEDELTA – struktura</span><span class="sxs-lookup"><span data-stu-id="4df08-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="4df08-103">Obsahuje informace, které obslužné rutiny symbolů o metodách, které byly přesunuty v důsledku úpravy.</span><span class="sxs-lookup"><span data-stu-id="4df08-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4df08-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="4df08-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4df08-105">Members</span></span>  
  
|<span data-ttu-id="4df08-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4df08-106">Member</span></span>|<span data-ttu-id="4df08-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4df08-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="4df08-108">Token metody metadat.</span><span class="sxs-lookup"><span data-stu-id="4df08-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="4df08-109">Počet řádků, který byl přesunut metodu.</span><span class="sxs-lookup"><span data-stu-id="4df08-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4df08-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4df08-110">Requirements</span></span>  
 <span data-ttu-id="4df08-111">**Záhlaví:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="4df08-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df08-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4df08-112">See also</span></span>

- [<span data-ttu-id="4df08-113">Struktury pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="4df08-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)

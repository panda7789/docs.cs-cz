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
ms.openlocfilehash: a1e83e4b8cb6603029f3b42b1a3b9ba4810c9039
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438009"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="fff9e-102">SYMLINEDELTA – struktura</span><span class="sxs-lookup"><span data-stu-id="fff9e-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="fff9e-103">Poskytuje informace obslužné rutině symbolů o metodách, které byly přesunuty v důsledku úprav.</span><span class="sxs-lookup"><span data-stu-id="fff9e-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fff9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fff9e-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="fff9e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="fff9e-105">Members</span></span>  
  
|<span data-ttu-id="fff9e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="fff9e-106">Member</span></span>|<span data-ttu-id="fff9e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fff9e-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="fff9e-108">Token metadat metody.</span><span class="sxs-lookup"><span data-stu-id="fff9e-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="fff9e-109">Počet řádků, které byla metoda přesunuta.</span><span class="sxs-lookup"><span data-stu-id="fff9e-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fff9e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fff9e-110">Requirements</span></span>  
 <span data-ttu-id="fff9e-111">**Hlavička:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="fff9e-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff9e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fff9e-112">See also</span></span>

- [<span data-ttu-id="fff9e-113">Struktury pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="fff9e-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)

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
ms.openlocfilehash: fb3b89d25b4c2e23c3980b167db4279246c4d27b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609297"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="3ab69-102">SYMLINEDELTA – struktura</span><span class="sxs-lookup"><span data-stu-id="3ab69-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="3ab69-103">Poskytuje informace obslužné rutině symbolů o metodách, které byly přesunuty v důsledku úprav.</span><span class="sxs-lookup"><span data-stu-id="3ab69-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ab69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ab69-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="3ab69-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3ab69-105">Members</span></span>  
  
|<span data-ttu-id="3ab69-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3ab69-106">Member</span></span>|<span data-ttu-id="3ab69-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3ab69-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="3ab69-108">Token metadat metody.</span><span class="sxs-lookup"><span data-stu-id="3ab69-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="3ab69-109">Počet řádků, které byla metoda přesunuta.</span><span class="sxs-lookup"><span data-stu-id="3ab69-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ab69-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ab69-110">Requirements</span></span>  
 <span data-ttu-id="3ab69-111">**Hlavička:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="3ab69-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ab69-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ab69-112">See also</span></span>

- [<span data-ttu-id="3ab69-113">Struktury úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="3ab69-113">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)

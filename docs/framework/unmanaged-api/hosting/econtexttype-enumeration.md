---
title: EContextType – výčet
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
ms.openlocfilehash: b93b27957cc715a5b4718dd9ef61cd11f4a39914
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493384"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="2c80f-102">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="2c80f-102">EContextType Enumeration</span></span>
<span data-ttu-id="2c80f-103">Popisuje kontext zabezpečení aktuálně zpracovávaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="2c80f-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c80f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c80f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="2c80f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2c80f-105">Members</span></span>  
  
|<span data-ttu-id="2c80f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2c80f-106">Member</span></span>|<span data-ttu-id="2c80f-107">Description</span><span class="sxs-lookup"><span data-stu-id="2c80f-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="2c80f-108">Určuje kontext v aktuálním vlákně v době, kdy modul CLR (Common Language Runtime) volá metodu [IHostSecurityManager:: GetSecurityContext –](ihostsecuritymanager-getsecuritycontext-method.md) , nebo kontext požadovaný modulem CLR ve volání metody [IHostSecurityManager:: SetSecurityContext –](ihostsecuritymanager-setsecuritycontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2c80f-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="2c80f-109">Označuje kontext, přes který má hostitel nižší oprávnění, jako je uvolňování paměti nebo konstruktory třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="2c80f-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c80f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c80f-110">Remarks</span></span>  
 <span data-ttu-id="2c80f-111">CLR poskytuje jednu z `EContextType` hodnot jako hodnotu parametru v volání `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` metod a.</span><span class="sxs-lookup"><span data-stu-id="2c80f-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c80f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c80f-112">Requirements</span></span>  
 <span data-ttu-id="2c80f-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c80f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c80f-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2c80f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c80f-115">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2c80f-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c80f-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c80f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c80f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c80f-117">See also</span></span>

- [<span data-ttu-id="2c80f-118">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c80f-118">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="2c80f-119">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c80f-119">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="2c80f-120">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="2c80f-120">Hosting Enumerations</span></span>](hosting-enumerations.md)

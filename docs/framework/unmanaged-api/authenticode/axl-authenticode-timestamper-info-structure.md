---
title: Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9eef89c9e560da65d670ffe59649b44a64f8da6a
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039611"
---
# <a name="axl_authenticode_timestamper_info-structure"></a><span data-ttu-id="69017-102">Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="69017-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="69017-103">Definuje informace o časovém razítku technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="69017-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69017-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69017-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="69017-105">Členové</span><span class="sxs-lookup"><span data-stu-id="69017-105">Members</span></span>  
  
|<span data-ttu-id="69017-106">Člen</span><span class="sxs-lookup"><span data-stu-id="69017-106">Member</span></span>|<span data-ttu-id="69017-107">Popis</span><span class="sxs-lookup"><span data-stu-id="69017-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="69017-108">Velikost této struktury</span><span class="sxs-lookup"><span data-stu-id="69017-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="69017-109">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="69017-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="69017-110">Algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="69017-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="69017-111">Čas časového razítka.</span><span class="sxs-lookup"><span data-stu-id="69017-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="69017-112">Kontext řetězu časového razítka.</span><span class="sxs-lookup"><span data-stu-id="69017-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="69017-113">Podívejte se na strukturu [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="69017-113">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69017-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69017-114">See also</span></span>

- [<span data-ttu-id="69017-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="69017-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

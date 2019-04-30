---
title: Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d82ed3299f967457fe967d096a238da6143751a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948917"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="f912e-102">Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="f912e-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="f912e-103">Definuje informace o čase stamper Authenticode.</span><span class="sxs-lookup"><span data-stu-id="f912e-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f912e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f912e-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="f912e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f912e-105">Members</span></span>  
  
|<span data-ttu-id="f912e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f912e-106">Member</span></span>|<span data-ttu-id="f912e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f912e-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="f912e-108">Velikost struktury.</span><span class="sxs-lookup"><span data-stu-id="f912e-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="f912e-109">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="f912e-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="f912e-110">Hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="f912e-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="f912e-111">Doba časového razítka.</span><span class="sxs-lookup"><span data-stu-id="f912e-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="f912e-112">Čas stamper kontextu řetězu.</span><span class="sxs-lookup"><span data-stu-id="f912e-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="f912e-113">Zobrazit [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) struktury.</span><span class="sxs-lookup"><span data-stu-id="f912e-113">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f912e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f912e-114">See also</span></span>

- [<span data-ttu-id="f912e-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="f912e-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

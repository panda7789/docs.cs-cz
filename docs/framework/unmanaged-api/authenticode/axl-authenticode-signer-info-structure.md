---
title: Struktura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 024837870aade6b0beb76fe758a571b15fd14d59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948974"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="cc5bf-102">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="cc5bf-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="cc5bf-103">Definuje informace o podpisu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="cc5bf-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc5bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc5bf-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="cc5bf-105">Členové</span><span class="sxs-lookup"><span data-stu-id="cc5bf-105">Members</span></span>  
  
|<span data-ttu-id="cc5bf-106">Člen</span><span class="sxs-lookup"><span data-stu-id="cc5bf-106">Member</span></span>|<span data-ttu-id="cc5bf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cc5bf-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="cc5bf-108">Velikost struktury.</span><span class="sxs-lookup"><span data-stu-id="cc5bf-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="cc5bf-109">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="cc5bf-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="cc5bf-110">Hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="cc5bf-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="cc5bf-111">Hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="cc5bf-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="cc5bf-112">Popis.</span><span class="sxs-lookup"><span data-stu-id="cc5bf-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="cc5bf-113">Adresa URL popisu.</span><span class="sxs-lookup"><span data-stu-id="cc5bf-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="cc5bf-114">Kontextu řetězu podpisu.</span><span class="sxs-lookup"><span data-stu-id="cc5bf-114">The chain context of the signer.</span></span> <span data-ttu-id="cc5bf-115">Zobrazit [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) struktury.</span><span class="sxs-lookup"><span data-stu-id="cc5bf-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc5bf-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc5bf-116">See also</span></span>

- [<span data-ttu-id="cc5bf-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="cc5bf-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

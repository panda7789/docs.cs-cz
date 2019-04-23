---
title: Struktura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 024837870aade6b0beb76fe758a571b15fd14d59
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107663"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="778e3-102">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="778e3-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="778e3-103">Definuje informace o podpisu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="778e3-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="778e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="778e3-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="778e3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="778e3-105">Members</span></span>  
  
|<span data-ttu-id="778e3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="778e3-106">Member</span></span>|<span data-ttu-id="778e3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="778e3-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="778e3-108">Velikost struktury.</span><span class="sxs-lookup"><span data-stu-id="778e3-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="778e3-109">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="778e3-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="778e3-110">Hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="778e3-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="778e3-111">Hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="778e3-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="778e3-112">Popis.</span><span class="sxs-lookup"><span data-stu-id="778e3-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="778e3-113">Adresa URL popisu.</span><span class="sxs-lookup"><span data-stu-id="778e3-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="778e3-114">Kontextu řetězu podpisu.</span><span class="sxs-lookup"><span data-stu-id="778e3-114">The chain context of the signer.</span></span> <span data-ttu-id="778e3-115">Zobrazit [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) struktury.</span><span class="sxs-lookup"><span data-stu-id="778e3-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="778e3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="778e3-116">See also</span></span>

- [<span data-ttu-id="778e3-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="778e3-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

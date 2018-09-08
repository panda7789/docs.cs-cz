---
title: Struktura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b9f54c7c57d122ac1214b9f31cc4e1d1cddd71c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44184321"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="59b0e-102">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="59b0e-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="59b0e-103">Definuje informace o podpisu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="59b0e-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59b0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59b0e-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="59b0e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="59b0e-105">Members</span></span>  
  
|<span data-ttu-id="59b0e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="59b0e-106">Member</span></span>|<span data-ttu-id="59b0e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="59b0e-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="59b0e-108">Velikost struktury.</span><span class="sxs-lookup"><span data-stu-id="59b0e-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="59b0e-109">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="59b0e-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="59b0e-110">Hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="59b0e-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="59b0e-111">Hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="59b0e-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="59b0e-112">Popis.</span><span class="sxs-lookup"><span data-stu-id="59b0e-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="59b0e-113">Adresa URL popisu.</span><span class="sxs-lookup"><span data-stu-id="59b0e-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="59b0e-114">Kontextu řetězu podpisu.</span><span class="sxs-lookup"><span data-stu-id="59b0e-114">The chain context of the signer.</span></span> <span data-ttu-id="59b0e-115">Zobrazit [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) struktury.</span><span class="sxs-lookup"><span data-stu-id="59b0e-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59b0e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="59b0e-116">See Also</span></span>  
 [<span data-ttu-id="59b0e-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="59b0e-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

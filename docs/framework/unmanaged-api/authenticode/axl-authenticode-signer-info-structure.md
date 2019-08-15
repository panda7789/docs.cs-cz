---
title: Struktura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c69be0de98e2996176e7360bae0bb0736c1a797
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038444"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="bca1a-102">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="bca1a-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="bca1a-103">Definuje přihlašovací údaje Authenticode.</span><span class="sxs-lookup"><span data-stu-id="bca1a-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bca1a-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="bca1a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="bca1a-105">Members</span></span>  
  
|<span data-ttu-id="bca1a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="bca1a-106">Member</span></span>|<span data-ttu-id="bca1a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bca1a-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="bca1a-108">Velikost této struktury</span><span class="sxs-lookup"><span data-stu-id="bca1a-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="bca1a-109">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="bca1a-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="bca1a-110">Algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="bca1a-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="bca1a-111">Hodnota hash</span><span class="sxs-lookup"><span data-stu-id="bca1a-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="bca1a-112">Popis.</span><span class="sxs-lookup"><span data-stu-id="bca1a-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="bca1a-113">Adresa URL popisu</span><span class="sxs-lookup"><span data-stu-id="bca1a-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="bca1a-114">Kontext řetězce podepsaného.</span><span class="sxs-lookup"><span data-stu-id="bca1a-114">The chain context of the signer.</span></span> <span data-ttu-id="bca1a-115">Podívejte se na strukturu [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="bca1a-115">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bca1a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bca1a-116">See also</span></span>

- [<span data-ttu-id="bca1a-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="bca1a-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

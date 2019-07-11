---
title: Struktura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 232c78db32aecd0ee1379d4d969fa0378db4159a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741353"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="ce46b-102">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="ce46b-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="ce46b-103">Definuje informace o podpisu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="ce46b-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce46b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce46b-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ce46b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ce46b-105">Members</span></span>  
  
|<span data-ttu-id="ce46b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ce46b-106">Member</span></span>|<span data-ttu-id="ce46b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ce46b-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="ce46b-108">Velikost struktury.</span><span class="sxs-lookup"><span data-stu-id="ce46b-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="ce46b-109">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="ce46b-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="ce46b-110">Hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="ce46b-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="ce46b-111">Hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="ce46b-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="ce46b-112">Popis.</span><span class="sxs-lookup"><span data-stu-id="ce46b-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="ce46b-113">Adresa URL popisu.</span><span class="sxs-lookup"><span data-stu-id="ce46b-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="ce46b-114">Kontextu řetězu podpisu.</span><span class="sxs-lookup"><span data-stu-id="ce46b-114">The chain context of the signer.</span></span> <span data-ttu-id="ce46b-115">Zobrazit [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) struktury.</span><span class="sxs-lookup"><span data-stu-id="ce46b-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce46b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce46b-116">See also</span></span>

- [<span data-ttu-id="ce46b-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ce46b-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

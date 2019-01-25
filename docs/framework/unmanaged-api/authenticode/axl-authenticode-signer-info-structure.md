---
title: Struktura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff50ee18dc3155bf784d6b752da8efc841aa6ce5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559434"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="bce90-102">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="bce90-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="bce90-103">Definuje informace o podpisu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="bce90-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bce90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bce90-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="bce90-105">Členové</span><span class="sxs-lookup"><span data-stu-id="bce90-105">Members</span></span>  
  
|<span data-ttu-id="bce90-106">Člen</span><span class="sxs-lookup"><span data-stu-id="bce90-106">Member</span></span>|<span data-ttu-id="bce90-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bce90-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="bce90-108">Velikost struktury.</span><span class="sxs-lookup"><span data-stu-id="bce90-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="bce90-109">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="bce90-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="bce90-110">Hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="bce90-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="bce90-111">Hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="bce90-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="bce90-112">Popis.</span><span class="sxs-lookup"><span data-stu-id="bce90-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="bce90-113">Adresa URL popisu.</span><span class="sxs-lookup"><span data-stu-id="bce90-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="bce90-114">Kontextu řetězu podpisu.</span><span class="sxs-lookup"><span data-stu-id="bce90-114">The chain context of the signer.</span></span> <span data-ttu-id="bce90-115">Zobrazit [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) struktury.</span><span class="sxs-lookup"><span data-stu-id="bce90-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bce90-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bce90-116">See also</span></span>
- [<span data-ttu-id="bce90-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="bce90-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

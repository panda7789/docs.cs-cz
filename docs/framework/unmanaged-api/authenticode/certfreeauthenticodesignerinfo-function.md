---
title: Funkce CertFreeAuthenticodeSignerInfo
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
ms.openlocfilehash: a233e0b8d17b9ee61b1991086f794c9fb20f89e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099838"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="08a8a-102">Funkce CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="08a8a-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="08a8a-103">Uvolní prostředky přidělené pro strukturu [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="08a8a-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08a8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08a8a-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08a8a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08a8a-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="08a8a-106">[in, out] Informace o podepisujícím, které se mají uvolnit</span><span class="sxs-lookup"><span data-stu-id="08a8a-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="08a8a-107">Podívejte se na strukturu [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="08a8a-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08a8a-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="08a8a-108">Return Value</span></span>  
 <span data-ttu-id="08a8a-109">`S_OK`, zda je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="08a8a-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="08a8a-110">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="08a8a-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08a8a-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08a8a-111">See also</span></span>

- [<span data-ttu-id="08a8a-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="08a8a-112">Authenticode</span></span>](index.md)

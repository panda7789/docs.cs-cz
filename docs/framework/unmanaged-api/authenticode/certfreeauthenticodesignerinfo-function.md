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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 357a2ca0ffc733adb14a21624cbe28fb754c8240
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776725"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="094e5-102">Funkce CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="094e5-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="094e5-103">Uvolní prostředky přidělené pro strukturu [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="094e5-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="094e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="094e5-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="094e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="094e5-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="094e5-106">[in, out] Informace o podepisujícím, které se mají uvolnit</span><span class="sxs-lookup"><span data-stu-id="094e5-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="094e5-107">Podívejte se na strukturu [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="094e5-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="094e5-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="094e5-108">Return Value</span></span>  
 <span data-ttu-id="094e5-109">`S_OK`Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="094e5-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="094e5-110">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="094e5-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="094e5-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="094e5-111">See also</span></span>

- [<span data-ttu-id="094e5-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="094e5-112">Authenticode</span></span>](index.md)

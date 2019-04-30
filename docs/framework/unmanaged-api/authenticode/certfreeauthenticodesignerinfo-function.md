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
ms.openlocfilehash: bdb764417b757cd7388c49d7e5cac9a960074820
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941614"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="4ba66-102">Funkce CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="4ba66-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="4ba66-103">Uvolní prostředky přidělené [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="4ba66-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ba66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ba66-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ba66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ba66-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="4ba66-106">[out v] Podepisující osoba informace uvolní.</span><span class="sxs-lookup"><span data-stu-id="4ba66-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="4ba66-107">Zobrazit [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="4ba66-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ba66-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4ba66-108">Return Value</span></span>  
 <span data-ttu-id="4ba66-109">`S_OK` Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="4ba66-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="4ba66-110">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4ba66-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ba66-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ba66-111">See also</span></span>

- [<span data-ttu-id="4ba66-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="4ba66-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

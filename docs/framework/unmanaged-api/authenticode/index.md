---
title: Authenticode (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ee0aca905c488bc3d285d69e431e79740bf8b7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623761"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="4c9a8-102">Authenticode (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="4c9a8-103">Podporuje modul vytváření a ověřování Authenticode XrML licence.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c9a8-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4c9a8-104">In This Section</span></span>  
 [<span data-ttu-id="4c9a8-105">Funkce _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="4c9a8-105">_AxlGetIssuerPublicKeyHash Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="4c9a8-106">Načte hodnotu hash SHA-1 veřejný klíč přidružený privátní klíč, který se používá k podepsání zadaný certifikát.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="4c9a8-107">Funkce _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="4c9a8-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="4c9a8-108">Vypočítá silným názvem token veřejného klíče z CSP publickeyblob – formátu.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="4c9a8-109">Funkce _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="4c9a8-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="4c9a8-110">Převede operace modulo a Exponent token veřejného klíče silného názvu.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="4c9a8-111">Funkce CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="4c9a8-111">CertFreeAuthenticodeSignerInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="4c9a8-112">Uvolní prostředky přidělené struktura AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="4c9a8-113">Funkce CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="4c9a8-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="4c9a8-114">Uvolní prostředky přidělené struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="4c9a8-115">Funkce CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="4c9a8-115">CertTimestampAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="4c9a8-116">Označit časovou značkou licenci Authenticode XrML vytvořené CertCreateAuthenticodeLicense.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="4c9a8-117">Funkce CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="4c9a8-117">CertVerifyAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="4c9a8-118">Ověří platnost licence k Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="4c9a8-119">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="4c9a8-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="4c9a8-120">Definuje informace o podpisu Authenticode.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="4c9a8-121">Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="4c9a8-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="4c9a8-122">Definuje informace o čase stamper Authenticode.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c9a8-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c9a8-123">See also</span></span>
- [<span data-ttu-id="4c9a8-124">Referenční informace o nespravovaném rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4c9a8-124">Unmanaged API Reference</span></span>](../../../../docs/framework/unmanaged-api/index.md)

---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
author: BrucePerlerMS
ms.openlocfilehash: 63af1c9a607cb9f81e2c0abf795ee2b3432cbf9c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397355"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="520f5-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="520f5-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="520f5-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="520f5-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="520f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="520f5-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="520f5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="520f5-105">Methods</span></span>  
 <span data-ttu-id="520f5-106">Třída AsymmetricSecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="520f5-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="520f5-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="520f5-107">Properties</span></span>  
 <span data-ttu-id="520f5-108">Třída AsymmetricSecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="520f5-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="520f5-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="520f5-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="520f5-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="520f5-110">Data type: string</span></span>  
  
 <span data-ttu-id="520f5-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="520f5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520f5-112">Pořadí zpráv šifrování a podepisování pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="520f5-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="520f5-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="520f5-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="520f5-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="520f5-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="520f5-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="520f5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520f5-116">Určuje, zda vytvoření vazby vyžaduje potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="520f5-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="520f5-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="520f5-117">Requirements</span></span>  
  
|<span data-ttu-id="520f5-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="520f5-118">MOF</span></span>|<span data-ttu-id="520f5-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="520f5-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="520f5-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="520f5-120">Namespace</span></span>|<span data-ttu-id="520f5-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="520f5-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="520f5-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="520f5-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

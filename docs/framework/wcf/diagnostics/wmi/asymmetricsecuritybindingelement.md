---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
author: BrucePerlerMS
ms.openlocfilehash: 63af1c9a607cb9f81e2c0abf795ee2b3432cbf9c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075054"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="32ffd-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="32ffd-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="32ffd-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="32ffd-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ffd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32ffd-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="32ffd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="32ffd-105">Methods</span></span>  
 <span data-ttu-id="32ffd-106">Třída AsymmetricSecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="32ffd-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="32ffd-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="32ffd-107">Properties</span></span>  
 <span data-ttu-id="32ffd-108">Třída AsymmetricSecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="32ffd-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="32ffd-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="32ffd-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="32ffd-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="32ffd-110">Data type: string</span></span>  
  
 <span data-ttu-id="32ffd-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="32ffd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32ffd-112">Pořadí zpráv šifrování a podepisování pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="32ffd-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="32ffd-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="32ffd-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="32ffd-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="32ffd-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="32ffd-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="32ffd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32ffd-116">Určuje, zda vytvoření vazby vyžaduje potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="32ffd-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32ffd-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32ffd-117">Requirements</span></span>  
  
|<span data-ttu-id="32ffd-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="32ffd-118">MOF</span></span>|<span data-ttu-id="32ffd-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="32ffd-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="32ffd-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="32ffd-120">Namespace</span></span>|<span data-ttu-id="32ffd-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="32ffd-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32ffd-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="32ffd-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

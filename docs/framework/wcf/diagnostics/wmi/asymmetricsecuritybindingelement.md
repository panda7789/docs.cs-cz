---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 076313548828f1fbce9c68b48c0fa7db9cca095f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185115"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="f0e37-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f0e37-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="f0e37-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f0e37-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0e37-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f0e37-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f0e37-105">Methods</span></span>  
 <span data-ttu-id="f0e37-106">Třída AsymmetricSecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="f0e37-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f0e37-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f0e37-107">Properties</span></span>  
 <span data-ttu-id="f0e37-108">Třída AsymmetricSecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f0e37-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="f0e37-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="f0e37-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="f0e37-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f0e37-110">Data type: string</span></span>  
  
 <span data-ttu-id="f0e37-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f0e37-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0e37-112">Pořadí zpráv šifrování a podepisování pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="f0e37-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="f0e37-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="f0e37-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="f0e37-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="f0e37-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="f0e37-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f0e37-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0e37-116">Určuje, zda vytvoření vazby vyžaduje potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="f0e37-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0e37-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0e37-117">Requirements</span></span>  
  
|<span data-ttu-id="f0e37-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="f0e37-118">MOF</span></span>|<span data-ttu-id="f0e37-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f0e37-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f0e37-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f0e37-120">Namespace</span></span>|<span data-ttu-id="f0e37-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f0e37-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0e37-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0e37-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

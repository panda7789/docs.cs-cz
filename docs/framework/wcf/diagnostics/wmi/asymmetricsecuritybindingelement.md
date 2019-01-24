---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: e968f5f2d7ffdb193b30762d32a47be3778b98dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621354"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="0dad2-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0dad2-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="0dad2-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0dad2-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dad2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0dad2-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0dad2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0dad2-105">Methods</span></span>  
 <span data-ttu-id="0dad2-106">Třída AsymmetricSecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="0dad2-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0dad2-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0dad2-107">Properties</span></span>  
 <span data-ttu-id="0dad2-108">Třída AsymmetricSecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="0dad2-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="0dad2-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="0dad2-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="0dad2-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0dad2-110">Data type: string</span></span>  
  
 <span data-ttu-id="0dad2-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0dad2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0dad2-112">Pořadí zpráv šifrování a podepisování pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="0dad2-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="0dad2-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="0dad2-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="0dad2-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="0dad2-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="0dad2-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0dad2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0dad2-116">Určuje, zda vytvoření vazby vyžaduje potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="0dad2-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dad2-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0dad2-117">Requirements</span></span>  
  
|<span data-ttu-id="0dad2-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="0dad2-118">MOF</span></span>|<span data-ttu-id="0dad2-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0dad2-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0dad2-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="0dad2-120">Namespace</span></span>|<span data-ttu-id="0dad2-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0dad2-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0dad2-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0dad2-122">See also</span></span>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

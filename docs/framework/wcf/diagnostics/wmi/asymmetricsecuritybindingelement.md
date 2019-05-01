---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 0f86fc1b410753b5ec100f0a7d43de9badd1401b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964200"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="3cb33-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3cb33-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="3cb33-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3cb33-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cb33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cb33-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3cb33-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3cb33-105">Methods</span></span>  
 <span data-ttu-id="3cb33-106">Třída AsymmetricSecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="3cb33-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3cb33-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3cb33-107">Properties</span></span>  
 <span data-ttu-id="3cb33-108">Třída AsymmetricSecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="3cb33-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="3cb33-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="3cb33-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="3cb33-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="3cb33-110">Data type: string</span></span>  
  
 <span data-ttu-id="3cb33-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3cb33-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3cb33-112">Pořadí zpráv šifrování a podepisování pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="3cb33-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="3cb33-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="3cb33-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="3cb33-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="3cb33-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="3cb33-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3cb33-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3cb33-116">Určuje, zda vytvoření vazby vyžaduje potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="3cb33-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cb33-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3cb33-117">Requirements</span></span>  
  
|<span data-ttu-id="3cb33-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="3cb33-118">MOF</span></span>|<span data-ttu-id="3cb33-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3cb33-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3cb33-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="3cb33-120">Namespace</span></span>|<span data-ttu-id="3cb33-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3cb33-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3cb33-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3cb33-122">See also</span></span>

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: f6effd533a205d0e8fd1421119e325f06b340dd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206795"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="e8909-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e8909-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="e8909-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e8909-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8909-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8909-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e8909-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e8909-105">Methods</span></span>  
 <span data-ttu-id="e8909-106">Element SymmetricSecurityBindingElement Třída nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="e8909-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e8909-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e8909-107">Properties</span></span>  
 <span data-ttu-id="e8909-108">Element SymmetricSecurityBindingElement třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="e8909-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="e8909-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="e8909-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="e8909-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e8909-110">Data type: string</span></span>  
  
 <span data-ttu-id="e8909-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e8909-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e8909-112">Pořadí zpráv šifrování a podepisování pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="e8909-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="e8909-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="e8909-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="e8909-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="e8909-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="e8909-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e8909-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e8909-116">Určuje, zda vytvoření vazby vyžaduje potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="e8909-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8909-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e8909-117">Requirements</span></span>  
  
|<span data-ttu-id="e8909-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="e8909-118">MOF</span></span>|<span data-ttu-id="e8909-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e8909-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e8909-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e8909-120">Namespace</span></span>|<span data-ttu-id="e8909-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e8909-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8909-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8909-122">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

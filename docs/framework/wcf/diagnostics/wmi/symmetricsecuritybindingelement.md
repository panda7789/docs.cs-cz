---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: 618899c80d1b22aaabc3c13fe1079137eaf10a93
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182499"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="df597-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="df597-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="df597-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="df597-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df597-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df597-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="df597-105">Metody</span><span class="sxs-lookup"><span data-stu-id="df597-105">Methods</span></span>  
 <span data-ttu-id="df597-106">Element SymmetricSecurityBindingElement Třída nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="df597-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="df597-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="df597-107">Properties</span></span>  
 <span data-ttu-id="df597-108">Element SymmetricSecurityBindingElement třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="df597-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="df597-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="df597-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="df597-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="df597-110">Data type: string</span></span>  
  
 <span data-ttu-id="df597-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="df597-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df597-112">Pořadí zpráv šifrování a podepisování pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="df597-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="df597-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="df597-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="df597-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="df597-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="df597-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="df597-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df597-116">Určuje, zda vytvoření vazby vyžaduje potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="df597-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df597-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df597-117">Requirements</span></span>  
  
|<span data-ttu-id="df597-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="df597-118">MOF</span></span>|<span data-ttu-id="df597-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="df597-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="df597-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="df597-120">Namespace</span></span>|<span data-ttu-id="df597-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="df597-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df597-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="df597-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

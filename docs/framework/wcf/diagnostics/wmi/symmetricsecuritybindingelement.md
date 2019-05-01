---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: f6effd533a205d0e8fd1421119e325f06b340dd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956712"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="70666-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="70666-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="70666-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="70666-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70666-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70666-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="70666-105">Metody</span><span class="sxs-lookup"><span data-stu-id="70666-105">Methods</span></span>  
 <span data-ttu-id="70666-106">Element SymmetricSecurityBindingElement Třída nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="70666-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="70666-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="70666-107">Properties</span></span>  
 <span data-ttu-id="70666-108">Element SymmetricSecurityBindingElement třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="70666-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="70666-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="70666-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="70666-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="70666-110">Data type: string</span></span>  
  
 <span data-ttu-id="70666-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="70666-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="70666-112">Pořadí zpráv šifrování a podepisování pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="70666-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="70666-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="70666-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="70666-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="70666-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="70666-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="70666-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="70666-116">Určuje, zda vytvoření vazby vyžaduje potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="70666-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70666-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70666-117">Requirements</span></span>  
  
|<span data-ttu-id="70666-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="70666-118">MOF</span></span>|<span data-ttu-id="70666-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="70666-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="70666-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="70666-120">Namespace</span></span>|<span data-ttu-id="70666-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="70666-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70666-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70666-122">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

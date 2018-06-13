---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7fc720f4f0be25a0cec25d979942af8472efa4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485053"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="d4c51-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d4c51-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="d4c51-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d4c51-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4c51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4c51-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d4c51-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d4c51-105">Methods</span></span>  
 <span data-ttu-id="d4c51-106">Třída třídu SymmetricSecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="d4c51-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d4c51-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d4c51-107">Properties</span></span>  
 <span data-ttu-id="d4c51-108">Třída třídu SymmetricSecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d4c51-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="d4c51-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="d4c51-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="d4c51-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d4c51-110">Data type: string</span></span>  
  
 <span data-ttu-id="d4c51-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d4c51-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4c51-112">Pořadí zpráva šifrování a podepisování pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="d4c51-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="d4c51-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="d4c51-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="d4c51-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="d4c51-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="d4c51-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d4c51-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4c51-116">Jestli vazby vyžaduje potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="d4c51-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4c51-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4c51-117">Requirements</span></span>  
  
|<span data-ttu-id="d4c51-118">MOF</span><span class="sxs-lookup"><span data-stu-id="d4c51-118">MOF</span></span>|<span data-ttu-id="d4c51-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d4c51-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d4c51-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d4c51-120">Namespace</span></span>|<span data-ttu-id="d4c51-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d4c51-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4c51-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4c51-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

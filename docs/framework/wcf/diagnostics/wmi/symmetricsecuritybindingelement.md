---
title: SymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7960ae9972490f2363b0f6f9942e947677c7d299
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="c5ccd-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c5ccd-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="c5ccd-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c5ccd-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5ccd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5ccd-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c5ccd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c5ccd-105">Methods</span></span>  
 <span data-ttu-id="c5ccd-106">Třída třídu SymmetricSecurityBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="c5ccd-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c5ccd-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c5ccd-107">Properties</span></span>  
 <span data-ttu-id="c5ccd-108">Třída třídu SymmetricSecurityBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="c5ccd-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="c5ccd-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="c5ccd-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="c5ccd-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="c5ccd-110">Data type: string</span></span>  
  
 <span data-ttu-id="c5ccd-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c5ccd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5ccd-112">Pořadí zpráva šifrování a podepisování pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="c5ccd-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="c5ccd-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="c5ccd-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="c5ccd-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="c5ccd-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="c5ccd-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c5ccd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5ccd-116">Jestli vazby vyžaduje potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="c5ccd-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5ccd-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5ccd-117">Requirements</span></span>  
  
|<span data-ttu-id="c5ccd-118">MOF</span><span class="sxs-lookup"><span data-stu-id="c5ccd-118">MOF</span></span>|<span data-ttu-id="c5ccd-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c5ccd-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c5ccd-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="c5ccd-120">Namespace</span></span>|<span data-ttu-id="c5ccd-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c5ccd-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5ccd-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5ccd-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

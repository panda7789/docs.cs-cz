---
title: OperationBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da0bc2ac9a4283ec9b23a1d4767f664de071ef47
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="2fc6d-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="2fc6d-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="2fc6d-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="2fc6d-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fc6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fc6d-104">Syntax</span></span>  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2fc6d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2fc6d-105">Methods</span></span>  
 <span data-ttu-id="2fc6d-106">Třída OperationBehaviorAttribute nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="2fc6d-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2fc6d-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2fc6d-107">Properties</span></span>  
 <span data-ttu-id="2fc6d-108">Třída OperationBehaviorAttribute má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2fc6d-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="2fc6d-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="2fc6d-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="2fc6d-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2fc6d-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="2fc6d-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2fc6d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc6d-112">Stav funkce automatického uvolnění pro parametry.</span><span class="sxs-lookup"><span data-stu-id="2fc6d-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="2fc6d-113">Zosobnění</span><span class="sxs-lookup"><span data-stu-id="2fc6d-113">Impersonation</span></span>  
 <span data-ttu-id="2fc6d-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="2fc6d-114">Data type: string</span></span>  
  
 <span data-ttu-id="2fc6d-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2fc6d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc6d-116">Informuje o úrovni zosobnění volající, který podporuje operaci.</span><span class="sxs-lookup"><span data-stu-id="2fc6d-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="2fc6d-117">ReleaseInstanceMode u atributu</span><span class="sxs-lookup"><span data-stu-id="2fc6d-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="2fc6d-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="2fc6d-118">Data type: string</span></span>  
  
 <span data-ttu-id="2fc6d-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2fc6d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc6d-120">Určuje, kdy v průběhu k vyvolání operace recyklace objektu.</span><span class="sxs-lookup"><span data-stu-id="2fc6d-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="2fc6d-121">Vlastnost TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="2fc6d-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="2fc6d-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2fc6d-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="2fc6d-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2fc6d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc6d-124">Označuje, zda automaticky potvrzení aktuální transakce, pokud dojde k žádné neošetřených výjimek.</span><span class="sxs-lookup"><span data-stu-id="2fc6d-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="2fc6d-125">Vlastností TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="2fc6d-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="2fc6d-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2fc6d-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="2fc6d-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2fc6d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc6d-128">Určuje, zda operace vyžaduje transakci.</span><span class="sxs-lookup"><span data-stu-id="2fc6d-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fc6d-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2fc6d-129">Requirements</span></span>  
  
|<span data-ttu-id="2fc6d-130">MOF</span><span class="sxs-lookup"><span data-stu-id="2fc6d-130">MOF</span></span>|<span data-ttu-id="2fc6d-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2fc6d-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2fc6d-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="2fc6d-132">Namespace</span></span>|<span data-ttu-id="2fc6d-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2fc6d-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2fc6d-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fc6d-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>

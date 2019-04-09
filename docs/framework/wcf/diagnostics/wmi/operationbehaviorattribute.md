---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 79601308c66abe43dd5a7f72bd2a05b9d2346c2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115801"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="36bd3-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="36bd3-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="36bd3-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="36bd3-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36bd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36bd3-104">Syntax</span></span>  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="36bd3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="36bd3-105">Methods</span></span>  
 <span data-ttu-id="36bd3-106">Třída OperationBehaviorAttribute nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="36bd3-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="36bd3-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="36bd3-107">Properties</span></span>  
 <span data-ttu-id="36bd3-108">Třída OperationBehaviorAttribute má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="36bd3-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="36bd3-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="36bd3-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="36bd3-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="36bd3-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="36bd3-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="36bd3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="36bd3-112">Stav funkce automatického dispose pro parametry.</span><span class="sxs-lookup"><span data-stu-id="36bd3-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="36bd3-113">Zosobnění</span><span class="sxs-lookup"><span data-stu-id="36bd3-113">Impersonation</span></span>  
 <span data-ttu-id="36bd3-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="36bd3-114">Data type: string</span></span>  
  
 <span data-ttu-id="36bd3-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="36bd3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="36bd3-116">Určuje úroveň představení volajícího, kterou operace podporuje.</span><span class="sxs-lookup"><span data-stu-id="36bd3-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="36bd3-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="36bd3-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="36bd3-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="36bd3-118">Data type: string</span></span>  
  
 <span data-ttu-id="36bd3-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="36bd3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="36bd3-120">Označuje, že když průběhu realizace operace má být objekt.</span><span class="sxs-lookup"><span data-stu-id="36bd3-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="36bd3-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="36bd3-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="36bd3-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="36bd3-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="36bd3-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="36bd3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="36bd3-124">Označuje, zda aktuální transakce potvrzena automaticky, pokud se nevyskytnou žádné nezpracované výjimky.</span><span class="sxs-lookup"><span data-stu-id="36bd3-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="36bd3-125">Vlastností TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="36bd3-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="36bd3-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="36bd3-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="36bd3-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="36bd3-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="36bd3-128">Určuje, zda operace vyžaduje transakci.</span><span class="sxs-lookup"><span data-stu-id="36bd3-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36bd3-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36bd3-129">Requirements</span></span>  
  
|<span data-ttu-id="36bd3-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="36bd3-130">MOF</span></span>|<span data-ttu-id="36bd3-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="36bd3-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="36bd3-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="36bd3-132">Namespace</span></span>|<span data-ttu-id="36bd3-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="36bd3-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36bd3-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36bd3-134">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>

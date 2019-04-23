---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 79601308c66abe43dd5a7f72bd2a05b9d2346c2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975153"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="bb7fd-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="bb7fd-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="bb7fd-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="bb7fd-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb7fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb7fd-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="bb7fd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bb7fd-105">Methods</span></span>  
 <span data-ttu-id="bb7fd-106">Třída OperationBehaviorAttribute nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bb7fd-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bb7fd-107">Properties</span></span>  
 <span data-ttu-id="bb7fd-108">Třída OperationBehaviorAttribute má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="bb7fd-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="bb7fd-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="bb7fd-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="bb7fd-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="bb7fd-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="bb7fd-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="bb7fd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb7fd-112">Stav funkce automatického dispose pro parametry.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="bb7fd-113">Zosobnění</span><span class="sxs-lookup"><span data-stu-id="bb7fd-113">Impersonation</span></span>  
 <span data-ttu-id="bb7fd-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="bb7fd-114">Data type: string</span></span>  
  
 <span data-ttu-id="bb7fd-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="bb7fd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb7fd-116">Určuje úroveň představení volajícího, kterou operace podporuje.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="bb7fd-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="bb7fd-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="bb7fd-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="bb7fd-118">Data type: string</span></span>  
  
 <span data-ttu-id="bb7fd-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="bb7fd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb7fd-120">Označuje, že když průběhu realizace operace má být objekt.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="bb7fd-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="bb7fd-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="bb7fd-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="bb7fd-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="bb7fd-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="bb7fd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb7fd-124">Označuje, zda aktuální transakce potvrzena automaticky, pokud se nevyskytnou žádné nezpracované výjimky.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="bb7fd-125">Vlastností TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="bb7fd-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="bb7fd-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="bb7fd-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="bb7fd-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="bb7fd-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb7fd-128">Určuje, zda operace vyžaduje transakci.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb7fd-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb7fd-129">Requirements</span></span>  
  
|<span data-ttu-id="bb7fd-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="bb7fd-130">MOF</span></span>|<span data-ttu-id="bb7fd-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="bb7fd-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bb7fd-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="bb7fd-132">Namespace</span></span>|<span data-ttu-id="bb7fd-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bb7fd-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb7fd-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb7fd-134">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>

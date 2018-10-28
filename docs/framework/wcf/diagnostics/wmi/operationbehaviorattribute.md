---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 6266713307846ab953299370835726958196fac1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185336"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="0d895-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="0d895-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="0d895-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="0d895-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d895-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d895-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="0d895-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0d895-105">Methods</span></span>  
 <span data-ttu-id="0d895-106">Třída OperationBehaviorAttribute nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="0d895-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0d895-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0d895-107">Properties</span></span>  
 <span data-ttu-id="0d895-108">Třída OperationBehaviorAttribute má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="0d895-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="0d895-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="0d895-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="0d895-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="0d895-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="0d895-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0d895-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d895-112">Stav funkce automatického dispose pro parametry.</span><span class="sxs-lookup"><span data-stu-id="0d895-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="0d895-113">Zosobnění</span><span class="sxs-lookup"><span data-stu-id="0d895-113">Impersonation</span></span>  
 <span data-ttu-id="0d895-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0d895-114">Data type: string</span></span>  
  
 <span data-ttu-id="0d895-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0d895-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d895-116">Určuje úroveň představení volajícího, kterou operace podporuje.</span><span class="sxs-lookup"><span data-stu-id="0d895-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="0d895-117">ReleaseInstanceMode u atributu</span><span class="sxs-lookup"><span data-stu-id="0d895-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="0d895-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0d895-118">Data type: string</span></span>  
  
 <span data-ttu-id="0d895-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0d895-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d895-120">Označuje, že když průběhu realizace operace má být objekt.</span><span class="sxs-lookup"><span data-stu-id="0d895-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="0d895-121">Vlastnost TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="0d895-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="0d895-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="0d895-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="0d895-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0d895-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d895-124">Označuje, zda aktuální transakce potvrzena automaticky, pokud se nevyskytnou žádné nezpracované výjimky.</span><span class="sxs-lookup"><span data-stu-id="0d895-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="0d895-125">Vlastností TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="0d895-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="0d895-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="0d895-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="0d895-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0d895-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d895-128">Určuje, zda operace vyžaduje transakci.</span><span class="sxs-lookup"><span data-stu-id="0d895-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d895-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d895-129">Requirements</span></span>  
  
|<span data-ttu-id="0d895-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="0d895-130">MOF</span></span>|<span data-ttu-id="0d895-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0d895-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0d895-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="0d895-132">Namespace</span></span>|<span data-ttu-id="0d895-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0d895-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d895-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d895-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>

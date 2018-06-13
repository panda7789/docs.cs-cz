---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: c2fb32c4c693cbfc487ce89b36f013398cbdb703
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485616"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="a8531-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="a8531-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="a8531-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="a8531-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8531-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8531-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a8531-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a8531-105">Methods</span></span>  
 <span data-ttu-id="a8531-106">Třída TransactionFlowBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="a8531-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a8531-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a8531-107">Properties</span></span>  
 <span data-ttu-id="a8531-108">Třída TransactionFlowBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a8531-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="a8531-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="a8531-109">IssuedTokens</span></span>  
 <span data-ttu-id="a8531-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a8531-110">Data type: string</span></span>  
  
 <span data-ttu-id="a8531-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a8531-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a8531-112">Určuje požadavek na hlavičku tokeny vydané zabezpečení (IssuedTokens z WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="a8531-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="a8531-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="a8531-113">TransactionProtocol</span></span>  
 <span data-ttu-id="a8531-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a8531-114">Data type: string</span></span>  
  
 <span data-ttu-id="a8531-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a8531-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a8531-116">Služba směrování transakcí používá protokol transakcí.</span><span class="sxs-lookup"><span data-stu-id="a8531-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="a8531-117">Transakce</span><span class="sxs-lookup"><span data-stu-id="a8531-117">Transactions</span></span>  
 <span data-ttu-id="a8531-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="a8531-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="a8531-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a8531-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a8531-120">Označuje, zda příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="a8531-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8531-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8531-121">Requirements</span></span>  
  
|<span data-ttu-id="a8531-122">MOF</span><span class="sxs-lookup"><span data-stu-id="a8531-122">MOF</span></span>|<span data-ttu-id="a8531-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a8531-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a8531-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="a8531-124">Namespace</span></span>|<span data-ttu-id="a8531-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a8531-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8531-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8531-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>

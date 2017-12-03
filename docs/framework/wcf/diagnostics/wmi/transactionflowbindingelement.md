---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa5394e874e35b80b01796642e18d69c71e867dc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="7a282-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="7a282-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="7a282-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="7a282-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a282-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a282-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7a282-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7a282-105">Methods</span></span>  
 <span data-ttu-id="7a282-106">Třída TransactionFlowBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="7a282-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7a282-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7a282-107">Properties</span></span>  
 <span data-ttu-id="7a282-108">Třída TransactionFlowBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7a282-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="7a282-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="7a282-109">IssuedTokens</span></span>  
 <span data-ttu-id="7a282-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7a282-110">Data type: string</span></span>  
  
 <span data-ttu-id="7a282-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7a282-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7a282-112">Určuje požadavek na hlavičku tokeny vydané zabezpečení (IssuedTokens z WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="7a282-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="7a282-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="7a282-113">TransactionProtocol</span></span>  
 <span data-ttu-id="7a282-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7a282-114">Data type: string</span></span>  
  
 <span data-ttu-id="7a282-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7a282-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7a282-116">Služba směrování transakcí používá protokol transakcí.</span><span class="sxs-lookup"><span data-stu-id="7a282-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="7a282-117">Transakce</span><span class="sxs-lookup"><span data-stu-id="7a282-117">Transactions</span></span>  
 <span data-ttu-id="7a282-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="7a282-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="7a282-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7a282-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7a282-120">Označuje, zda příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="7a282-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a282-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a282-121">Requirements</span></span>  
  
|<span data-ttu-id="7a282-122">MOF</span><span class="sxs-lookup"><span data-stu-id="7a282-122">MOF</span></span>|<span data-ttu-id="7a282-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7a282-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7a282-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="7a282-124">Namespace</span></span>|<span data-ttu-id="7a282-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7a282-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a282-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a282-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>

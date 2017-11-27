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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c65eb1689d1411cb9083967b9a29c946b7568b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="4e1ce-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="4e1ce-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="4e1ce-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="4e1ce-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e1ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e1ce-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4e1ce-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4e1ce-105">Methods</span></span>  
 <span data-ttu-id="4e1ce-106">Třída TransactionFlowBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="4e1ce-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4e1ce-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4e1ce-107">Properties</span></span>  
 <span data-ttu-id="4e1ce-108">Třída TransactionFlowBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4e1ce-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="4e1ce-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="4e1ce-109">IssuedTokens</span></span>  
 <span data-ttu-id="4e1ce-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4e1ce-110">Data type: string</span></span>  
  
 <span data-ttu-id="4e1ce-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e1ce-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e1ce-112">Určuje požadavek na hlavičku tokeny vydané zabezpečení (IssuedTokens z WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="4e1ce-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="4e1ce-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="4e1ce-113">TransactionProtocol</span></span>  
 <span data-ttu-id="4e1ce-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4e1ce-114">Data type: string</span></span>  
  
 <span data-ttu-id="4e1ce-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e1ce-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e1ce-116">Služba směrování transakcí používá protokol transakcí.</span><span class="sxs-lookup"><span data-stu-id="4e1ce-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="4e1ce-117">Transakce</span><span class="sxs-lookup"><span data-stu-id="4e1ce-117">Transactions</span></span>  
 <span data-ttu-id="4e1ce-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="4e1ce-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="4e1ce-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e1ce-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e1ce-120">Označuje, zda příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="4e1ce-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e1ce-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e1ce-121">Requirements</span></span>  
  
|<span data-ttu-id="4e1ce-122">MOF</span><span class="sxs-lookup"><span data-stu-id="4e1ce-122">MOF</span></span>|<span data-ttu-id="4e1ce-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4e1ce-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4e1ce-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="4e1ce-124">Namespace</span></span>|<span data-ttu-id="4e1ce-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4e1ce-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e1ce-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e1ce-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>

---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: d0311837ebb8112d9492fb548492bcd3e10230e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514567"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="b0330-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="b0330-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="b0330-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="b0330-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0330-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0330-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b0330-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b0330-105">Methods</span></span>  
 <span data-ttu-id="b0330-106">Třídy TransactionFlowBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="b0330-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b0330-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b0330-107">Properties</span></span>  
 <span data-ttu-id="b0330-108">Třídy TransactionFlowBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="b0330-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="b0330-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="b0330-109">IssuedTokens</span></span>  
 <span data-ttu-id="b0330-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="b0330-110">Data type: string</span></span>  
  
 <span data-ttu-id="b0330-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b0330-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0330-112">Určuje požadavek pro hlavičku tokeny vydané zabezpečení (IssuedTokens z WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="b0330-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="b0330-113">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="b0330-113">TransactionProtocol</span></span>  
 <span data-ttu-id="b0330-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="b0330-114">Data type: string</span></span>  
  
 <span data-ttu-id="b0330-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b0330-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0330-116">Protokol transakce použitý službou pro tok transakcí.</span><span class="sxs-lookup"><span data-stu-id="b0330-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="b0330-117">Transakce</span><span class="sxs-lookup"><span data-stu-id="b0330-117">Transactions</span></span>  
 <span data-ttu-id="b0330-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="b0330-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="b0330-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b0330-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0330-120">Označuje, zda je příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="b0330-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0330-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0330-121">Requirements</span></span>  
  
|<span data-ttu-id="b0330-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="b0330-122">MOF</span></span>|<span data-ttu-id="b0330-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b0330-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b0330-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b0330-124">Namespace</span></span>|<span data-ttu-id="b0330-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b0330-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0330-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0330-126">See also</span></span>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>

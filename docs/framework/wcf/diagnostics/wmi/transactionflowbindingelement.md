---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: a58d5620abbb636480ceea3020552246ae284842
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771592"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="c5d56-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="c5d56-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="c5d56-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="c5d56-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5d56-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c5d56-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c5d56-105">Methods</span></span>  
 <span data-ttu-id="c5d56-106">Třídy TransactionFlowBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="c5d56-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c5d56-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c5d56-107">Properties</span></span>  
 <span data-ttu-id="c5d56-108">Třídy TransactionFlowBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="c5d56-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="c5d56-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="c5d56-109">IssuedTokens</span></span>  
 <span data-ttu-id="c5d56-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="c5d56-110">Data type: string</span></span>  
  
 <span data-ttu-id="c5d56-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c5d56-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5d56-112">Určuje požadavek pro hlavičku tokeny vydané zabezpečení (IssuedTokens z WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="c5d56-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="c5d56-113">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="c5d56-113">TransactionProtocol</span></span>  
 <span data-ttu-id="c5d56-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="c5d56-114">Data type: string</span></span>  
  
 <span data-ttu-id="c5d56-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c5d56-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5d56-116">Protokol transakce použitý službou pro tok transakcí.</span><span class="sxs-lookup"><span data-stu-id="c5d56-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="c5d56-117">Transakce</span><span class="sxs-lookup"><span data-stu-id="c5d56-117">Transactions</span></span>  
 <span data-ttu-id="c5d56-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="c5d56-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="c5d56-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c5d56-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5d56-120">Označuje, zda je příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="c5d56-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5d56-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5d56-121">Requirements</span></span>  
  
|<span data-ttu-id="c5d56-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="c5d56-122">MOF</span></span>|<span data-ttu-id="c5d56-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c5d56-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c5d56-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="c5d56-124">Namespace</span></span>|<span data-ttu-id="c5d56-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c5d56-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5d56-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5d56-126">See also</span></span>

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>

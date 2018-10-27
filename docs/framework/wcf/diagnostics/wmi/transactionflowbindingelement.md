---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 027ace6ea9fc2a0e5ce63efa84e1a49c0ed2cd0a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188024"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="2db5c-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="2db5c-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="2db5c-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="2db5c-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2db5c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2db5c-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2db5c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2db5c-105">Methods</span></span>  
 <span data-ttu-id="2db5c-106">Třídy TransactionFlowBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="2db5c-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2db5c-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2db5c-107">Properties</span></span>  
 <span data-ttu-id="2db5c-108">Třídy TransactionFlowBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2db5c-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="2db5c-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="2db5c-109">IssuedTokens</span></span>  
 <span data-ttu-id="2db5c-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="2db5c-110">Data type: string</span></span>  
  
 <span data-ttu-id="2db5c-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2db5c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2db5c-112">Určuje požadavek pro hlavičku tokeny vydané zabezpečení (IssuedTokens z WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="2db5c-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="2db5c-113">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="2db5c-113">TransactionProtocol</span></span>  
 <span data-ttu-id="2db5c-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="2db5c-114">Data type: string</span></span>  
  
 <span data-ttu-id="2db5c-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2db5c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2db5c-116">Protokol transakce použitý službou pro tok transakcí.</span><span class="sxs-lookup"><span data-stu-id="2db5c-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="2db5c-117">Transakce</span><span class="sxs-lookup"><span data-stu-id="2db5c-117">Transactions</span></span>  
 <span data-ttu-id="2db5c-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="2db5c-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="2db5c-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2db5c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2db5c-120">Označuje, zda je příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="2db5c-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2db5c-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2db5c-121">Requirements</span></span>  
  
|<span data-ttu-id="2db5c-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="2db5c-122">MOF</span></span>|<span data-ttu-id="2db5c-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2db5c-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2db5c-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="2db5c-124">Namespace</span></span>|<span data-ttu-id="2db5c-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2db5c-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2db5c-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="2db5c-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>

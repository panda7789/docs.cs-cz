---
title: "Porovnání transakcí u modelů COM+ a ServiceModel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e3df31060a9c71e0b2868aa34373bca221fa79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a><span data-ttu-id="4f010-102">Porovnání transakcí u modelů COM+ a ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4f010-102">Comparing Transactions in COM+ and ServiceModel</span></span>
<span data-ttu-id="4f010-103">Toto téma popisuje, jak k simulaci chování transakcí modelu COM + službu pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] atributy <xref:System.ServiceModel> poskytuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="4f010-103">This topic discusses how to simulate the behavior of a transactional COM+ service using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
## <a name="emulating-com-using-servicemodel-attributes"></a><span data-ttu-id="4f010-104">Emulace modelu COM + pomocí atributy ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4f010-104">Emulating COM+ Using ServiceModel Attributes</span></span>  
 <span data-ttu-id="4f010-105">Následující tabulka porovnává <xref:System.EnterpriseServices.TransactionOption> použít k vytvoření výčtu `EnterpriseServices` transakce a jak se korelaci do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] atributy <xref:System.ServiceModel> poskytuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="4f010-105">The following table compares the <xref:System.EnterpriseServices.TransactionOption> enumeration used to create an `EnterpriseServices` transaction and how they correlate to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
|<span data-ttu-id="4f010-106">Atribut modelu COM +</span><span class="sxs-lookup"><span data-stu-id="4f010-106">COM+ attribute</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="4f010-107">atributy</span><span class="sxs-lookup"><span data-stu-id="4f010-107"> attributes</span></span>|  
|---------------------|------------------------------------------------------------------------|  
|<span data-ttu-id="4f010-108">RequiresNew</span><span class="sxs-lookup"><span data-stu-id="4f010-108">RequiresNew</span></span>|<span data-ttu-id="4f010-109"><xref:System.ServiceModel.TransactionFlowAttribute>je nastavena na <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span><span class="sxs-lookup"><span data-stu-id="4f010-109"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span></span><br /><br /> <span data-ttu-id="4f010-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>je `true`.</span><span class="sxs-lookup"><span data-stu-id="4f010-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="4f010-111">`TransactionFlow` Atribut v prvku vazby je `false`.</span><span class="sxs-lookup"><span data-stu-id="4f010-111">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="4f010-112">Požadováno</span><span class="sxs-lookup"><span data-stu-id="4f010-112">Required</span></span>|<span data-ttu-id="4f010-113"><xref:System.ServiceModel.TransactionFlowAttribute>je nastavena na <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span><span class="sxs-lookup"><span data-stu-id="4f010-113"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span></span><br /><br /> <span data-ttu-id="4f010-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>je `true`.</span><span class="sxs-lookup"><span data-stu-id="4f010-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="4f010-115">`TransactionFlow` Atribut v prvku vazby je `true`.</span><span class="sxs-lookup"><span data-stu-id="4f010-115">The `TransactionFlow` attribute in the binding element is `true`.</span></span>|  
|<span data-ttu-id="4f010-116">Podporováno</span><span class="sxs-lookup"><span data-stu-id="4f010-116">Supported</span></span>|<span data-ttu-id="4f010-117">Neexistuje žádný ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="4f010-117">There is no direct equivalent.</span></span> <span data-ttu-id="4f010-118">Obecně platí, musí přijmout nastavení chování `Required` místo.</span><span class="sxs-lookup"><span data-stu-id="4f010-118">In general, you should adopt the behavior specified for `Required` instead.</span></span>|  
|<span data-ttu-id="4f010-119">NotSupported</span><span class="sxs-lookup"><span data-stu-id="4f010-119">NotSupported</span></span>|<span data-ttu-id="4f010-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>je `false`.</span><span class="sxs-lookup"><span data-stu-id="4f010-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `false`.</span></span><br /><br /> <span data-ttu-id="4f010-121">`TransactionFlow` Atribut v prvku vazby je `false`.</span><span class="sxs-lookup"><span data-stu-id="4f010-121">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="4f010-122">zakázáno</span><span class="sxs-lookup"><span data-stu-id="4f010-122">Disabled</span></span>|<span data-ttu-id="4f010-123">Neexistuje žádný ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="4f010-123">There is no direct equivalent.</span></span> <span data-ttu-id="4f010-124">Obecně platí, musí přijmout nastavení chování `NotSupported` místo.</span><span class="sxs-lookup"><span data-stu-id="4f010-124">In general, you should adopt the behavior specified for `NotSupported` instead.</span></span>|

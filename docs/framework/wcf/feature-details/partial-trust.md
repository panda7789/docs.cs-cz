---
title: Částečná důvěryhodnost
ms.date: 03/30/2017
ms.assetid: 489b1587-9909-4d0e-8c1a-5e83c8f8292b
ms.openlocfilehash: f4eace87593f2b4c45101bafa0843998a093cbd5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579147"
---
# <a name="partial-trust"></a><span data-ttu-id="712b6-102">Částečná důvěryhodnost</span><span class="sxs-lookup"><span data-stu-id="712b6-102">Partial Trust</span></span>

<span data-ttu-id="712b6-103">Počínaje .NET Framework 3,5 mohou částečně důvěryhodní volající přistupovat k veřejným typům a metodám implementovaným v <xref:System.ServiceModel> , <xref:System.Runtime.Serialization> a <xref:System.ServiceModel.Web> .</span><span class="sxs-lookup"><span data-stu-id="712b6-103">Starting with the .NET Framework 3.5, partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="712b6-104">Tato část popisuje podporované scénáře použití Windows Communication Foundation (WCF) v částečně důvěryhodné aplikaci a také omezenou podmnožinu funkcí WCF, která je dostupná pro aplikace spuštěné s omezenými oprávněními zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="712b6-104">This section describes supported scenarios for using Windows Communication Foundation (WCF) within a partially trusted application as well as the limited subset of WCF functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="712b6-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="712b6-105">In This Section</span></span>  
 [<span data-ttu-id="712b6-106">Podporované scénáře nasazení</span><span class="sxs-lookup"><span data-stu-id="712b6-106">Supported Deployment Scenarios</span></span>](supported-deployment-scenarios.md)  
 <span data-ttu-id="712b6-107">Popisuje hlavní scénáře s částečnou důvěryhodností pro provozování WCF.</span><span class="sxs-lookup"><span data-stu-id="712b6-107">Describes the main partial trust scenarios for running WCF.</span></span>  
  
 [<span data-ttu-id="712b6-108">Kompatibilita funkcí s částečnou důvěryhodností</span><span class="sxs-lookup"><span data-stu-id="712b6-108">Partial Trust Feature Compatibility</span></span>](partial-trust-feature-compatibility.md)  
 <span data-ttu-id="712b6-109">Popisuje funkce služby WCF, které nelze použít s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="712b6-109">Describes the WCF features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="712b6-110">Osvědčené postupy pro částečnou důvěryhodnost</span><span class="sxs-lookup"><span data-stu-id="712b6-110">Partial Trust Best Practices</span></span>](partial-trust-best-practices.md)  
 <span data-ttu-id="712b6-111">Obsahuje osvědčené postupy pro použití WCF v částečně důvěryhodných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="712b6-111">Contains best practices for using WCF in partially trusted applications.</span></span>

---
title: "Kryptografická flexibilita v zabezpečení WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7d99ada67255d0ced8bbabc2ab6fc645e6ba9e35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="0bb86-102">Kryptografická flexibilita v zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="0bb86-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="0bb86-103">Tento příklad ukazuje, jak určit v algoritmu standardní nebo vlastní k zajištění kryptografických agilní implementace v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="0bb86-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service.</span></span> <span data-ttu-id="0bb86-104">Ukázka se skládá z následujících projektech:</span><span class="sxs-lookup"><span data-stu-id="0bb86-104">The sample is composed of the following projects:</span></span>  
  
 <span data-ttu-id="0bb86-105">Služba</span><span class="sxs-lookup"><span data-stu-id="0bb86-105">Service</span></span>  
 <span data-ttu-id="0bb86-106">Toto je vlastním hostováním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba, která implementuje `ICalculator` rozhraní a zabezpečuje koncový bod pomocí <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> s zabezpečené relace a spolehlivé relace zakázán.</span><span class="sxs-lookup"><span data-stu-id="0bb86-106">This is a self-hosted [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="0bb86-107">Služba definuje vlastní `SecurityAlgorithmSuite` třídu k určení kryptografické algoritmy, které má být použit pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="0bb86-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
 <span data-ttu-id="0bb86-108">Klient</span><span class="sxs-lookup"><span data-stu-id="0bb86-108">Client</span></span>  
 <span data-ttu-id="0bb86-109">Toto je [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]klienta, který službu používá po úspěšném ověření.</span><span class="sxs-lookup"><span data-stu-id="0bb86-109">This is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]client that accesses the service after successful authentication.</span></span> <span data-ttu-id="0bb86-110">Vyvolá operace vystavené `ICalculator` rozhraní a implementují službu.</span><span class="sxs-lookup"><span data-stu-id="0bb86-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="0bb86-111">Klient také definuje stejné vlastní `SecurityAlgorithmSuite` třídu k určení kryptografické algoritmy, které má být použit pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="0bb86-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="0bb86-112">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="0bb86-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="0bb86-113">Otevřete řešení CryptoAgility.sln v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0bb86-113">Open the CryptoAgility.sln solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="0bb86-114">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="0bb86-114">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="0bb86-115">Otevřete [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Service\bin a spusťte soubor service.exe s oprávněními správce service.exe kliknete pravým tlačítkem a výběrem **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="0bb86-115">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="0bb86-116">Přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Client\bin a spusťte soubor client.exe normálně.</span><span class="sxs-lookup"><span data-stu-id="0bb86-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0bb86-117">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="0bb86-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0bb86-118">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0bb86-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0bb86-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0bb86-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0bb86-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0bb86-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="0bb86-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bb86-121">See Also</span></span>  
 [<span data-ttu-id="0bb86-122">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0bb86-122">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)

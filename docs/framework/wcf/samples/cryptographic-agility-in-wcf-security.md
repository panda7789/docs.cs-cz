---
title: Kryptografická flexibilita v zabezpečení WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
author: BrucePerlerMS
ms.openlocfilehash: df40a87e2fe58b93a963d53fc79f88bbc7bdb805
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2018
ms.locfileid: "47421200"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="c02f7-102">Kryptografická flexibilita v zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="c02f7-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="c02f7-103">Tato ukázka předvádí, jak určit v algoritmu standardní nebo vlastní poskytují kryptografické agilní implementace klienta Windows Communication Foundation (WCF) a služby.</span><span class="sxs-lookup"><span data-stu-id="c02f7-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="c02f7-104">Ukázka se skládá z následující projekty:</span><span class="sxs-lookup"><span data-stu-id="c02f7-104">The sample is composed of the following projects:</span></span>  
  
 <span data-ttu-id="c02f7-105">Služba</span><span class="sxs-lookup"><span data-stu-id="c02f7-105">Service</span></span>  
 <span data-ttu-id="c02f7-106">Toto je v místním prostředí služby WCF, který implementuje `ICalculator` rozhraní a zabezpečuje pomocí koncového bodu <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> zabezpečenou relaci a stabilní relaci zakázán.</span><span class="sxs-lookup"><span data-stu-id="c02f7-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="c02f7-107">Služba definuje vlastní `SecurityAlgorithmSuite` tak, aby určovala kryptografické algoritmy pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="c02f7-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
 <span data-ttu-id="c02f7-108">Klient</span><span class="sxs-lookup"><span data-stu-id="c02f7-108">Client</span></span>  
 <span data-ttu-id="c02f7-109">Toto je WCFclient, který službu používá po úspěšném ověření.</span><span class="sxs-lookup"><span data-stu-id="c02f7-109">This is a WCFclient that accesses the service after successful authentication.</span></span> <span data-ttu-id="c02f7-110">Vyvolá operace vystavené `ICalculator` rozhraní a službou implementována.</span><span class="sxs-lookup"><span data-stu-id="c02f7-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="c02f7-111">Klient také definuje stejné vlastní `SecurityAlgorithmSuite` tak, aby určovala kryptografické algoritmy pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="c02f7-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="c02f7-112">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="c02f7-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="c02f7-113">Otevřete řešení CryptoAgility.sln v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c02f7-113">Open the CryptoAgility.sln solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="c02f7-114">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="c02f7-114">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="c02f7-115">Otevřít [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Service\bin a spusťte soubor service.exe s oprávněními správce tak, že service.exe kliknete pravým tlačítkem a vyberete **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="c02f7-115">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="c02f7-116">Přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Client\bin a spusťte soubor client.exe normálně.</span><span class="sxs-lookup"><span data-stu-id="c02f7-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c02f7-117">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="c02f7-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c02f7-118">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c02f7-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c02f7-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c02f7-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c02f7-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c02f7-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="c02f7-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c02f7-121">See Also</span></span>  
 [<span data-ttu-id="c02f7-122">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c02f7-122">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)

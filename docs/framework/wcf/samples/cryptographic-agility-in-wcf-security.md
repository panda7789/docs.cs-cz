---
title: Kryptografická flexibilita v zabezpečení WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
author: BrucePerlerMS
ms.openlocfilehash: ebc1b51e2e16f1414f2ed1f4a49a69e26583a17b
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847346"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="6d3e3-102">Kryptografická flexibilita v zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="6d3e3-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="6d3e3-103">Tato ukázka předvádí, jak určit v algoritmu standardní nebo vlastní poskytují kryptografické agilní implementace klienta Windows Communication Foundation (WCF) a služby.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="6d3e3-104">Ukázka se skládá z následující projekty:</span><span class="sxs-lookup"><span data-stu-id="6d3e3-104">The sample is composed of the following projects:</span></span>

 <span data-ttu-id="6d3e3-105">Služby, to je v místním prostředí služby WCF, který implementuje `ICalculator` rozhraní a zabezpečuje pomocí koncového bodu <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> zabezpečenou relaci a stabilní relaci zakázán.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-105">Service This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="6d3e3-106">Služba definuje vlastní `SecurityAlgorithmSuite` tak, aby určovala kryptografické algoritmy pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-106">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

 <span data-ttu-id="6d3e3-107">Klient jedná WCFclient, který službu používá po úspěšném ověření.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-107">Client This is a WCFclient that accesses the service after successful authentication.</span></span> <span data-ttu-id="6d3e3-108">Vyvolá operace vystavené `ICalculator` rozhraní a službou implementována.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-108">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="6d3e3-109">Klient také definuje stejné vlastní `SecurityAlgorithmSuite` tak, aby určovala kryptografické algoritmy pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-109">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="6d3e3-110">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="6d3e3-110">To use this sample</span></span>

1.  <span data-ttu-id="6d3e3-111">Otevřete CryptoAgility.sln řešení v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-111">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2.  <span data-ttu-id="6d3e3-112">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-112">Press CTRL+SHIFT+B to build the solution.</span></span>

3.  <span data-ttu-id="6d3e3-113">Otevřít [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Service\bin a spusťte soubor service.exe s oprávněními správce tak, že service.exe kliknete pravým tlačítkem a vyberete **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-113">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4.  <span data-ttu-id="6d3e3-114">Přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Client\bin a spusťte soubor client.exe normálně.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-114">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="6d3e3-115">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6d3e3-116">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6d3e3-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6d3e3-117">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6d3e3-118">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="6d3e3-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d3e3-119">See Also</span></span>  
 [<span data-ttu-id="6d3e3-120">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6d3e3-120">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)

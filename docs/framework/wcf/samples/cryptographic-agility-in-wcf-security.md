---
title: Kryptografická flexibilita v zabezpečení WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 2dbacd53876ded76ea212dd5656cd2dded4a6e48
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714928"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="f5bf3-102">Kryptografická flexibilita v zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="f5bf3-102">Cryptographic agility in WCF security</span></span>

<span data-ttu-id="f5bf3-103">Tento příklad ukazuje, jak zadat standardní/vlastní algoritmus pro zajištění kryptografické implementace v Windows Communication Foundation (WCF) klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="f5bf3-104">Ukázka se skládá z následujících projektů:</span><span class="sxs-lookup"><span data-stu-id="f5bf3-104">The sample is composed of the following projects:</span></span>

<span data-ttu-id="f5bf3-105">**Service**</span><span class="sxs-lookup"><span data-stu-id="f5bf3-105">**Service**</span></span>

<span data-ttu-id="f5bf3-106">Toto je Samoobslužná služba WCF, která implementuje rozhraní `ICalculator` a zabezpečení koncového bodu pomocí <xref:System.ServiceModel.WSHttpBinding> se zakázanou zabezpečenou relací a spolehlivou relací.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <xref:System.ServiceModel.WSHttpBinding> with secure session and reliable session disabled.</span></span> <span data-ttu-id="f5bf3-107">Služba definuje vlastní třídu `SecurityAlgorithmSuite` pro určení kryptografických algoritmů, které se mají použít pro zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

<span data-ttu-id="f5bf3-108">**Klient**</span><span class="sxs-lookup"><span data-stu-id="f5bf3-108">**Client**</span></span>

<span data-ttu-id="f5bf3-109">Toto je klient služby WCF, který po úspěšném ověření přistupuje ke službě.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-109">This is a WCF client that accesses the service after successful authentication.</span></span> <span data-ttu-id="f5bf3-110">Vyvolá operace vystavené rozhraním `ICalculator` a implementované službou.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="f5bf3-111">Klient také definuje stejnou vlastní třídu `SecurityAlgorithmSuite` pro určení kryptografických algoritmů, které se mají použít pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

## <a name="to-use-this-sample"></a><span data-ttu-id="f5bf3-112">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="f5bf3-112">To use this sample</span></span>

1. <span data-ttu-id="f5bf3-113">Otevřete řešení CryptoAgility. sln v aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-113">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2. <span data-ttu-id="f5bf3-114">Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-114">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="f5bf3-115">Otevřete Průzkumníka souborů a přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Service\bin a spusťte soubor Service. exe s oprávněními správce tak, že kliknete pravým tlačítkem na Service. exe a vyberete **Spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-115">Open File Explorer and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4. <span data-ttu-id="f5bf3-116">Přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Client\bin a normálně spusťte soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5bf3-117">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f5bf3-118">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f5bf3-119">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f5bf3-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f5bf3-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a><span data-ttu-id="f5bf3-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5bf3-121">See also</span></span>

- [<span data-ttu-id="f5bf3-122">Windows Communication Foundation zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f5bf3-122">Windows Communication Foundation Security</span></span>](../feature-details/security.md)

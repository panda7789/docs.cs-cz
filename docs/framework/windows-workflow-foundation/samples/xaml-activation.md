---
title: Aktivace XAML
ms.date: 03/30/2017
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
ms.openlocfilehash: 8621b0ea7b390c81e76ac7eeedb0b547b44320d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517709"
---
# <a name="xaml-activation"></a><span data-ttu-id="f36b2-102">Aktivace XAML</span><span class="sxs-lookup"><span data-stu-id="f36b2-102">XAML Activation</span></span>
<span data-ttu-id="f36b2-103">Tento příklad ukazuje, jak k hostování deklarativní pracovní postup ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="f36b2-103">This sample demonstrates how to host a declarative workflow in IIS.</span></span> <span data-ttu-id="f36b2-104">Ukázka je základní pracovní postup volá `EchoService` má jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="f36b2-104">The sample is a basic workflow called `EchoService` that has one operation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f36b2-105">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="f36b2-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f36b2-106">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f36b2-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f36b2-107">Pokud tento adresář neexistuje, přejděte k (stránce pro stažení) Chcete-li stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f36b2-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f36b2-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f36b2-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f36b2-109">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="f36b2-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f36b2-110">Otevřete řešení XAMLActivation.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f36b2-110">Open the XAMLActivation.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="f36b2-111">Sestavte řešení stisknutím **F5**.</span><span class="sxs-lookup"><span data-stu-id="f36b2-111">Build the solution by pressing **F5**.</span></span>  
  
3.  <span data-ttu-id="f36b2-112">Spusťte WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="f36b2-112">Run WcfTestClient.exe.</span></span> <span data-ttu-id="f36b2-113">Z příkazového řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="f36b2-113">From a command prompt, type in the following:</span></span>  
  
    1.  <span data-ttu-id="f36b2-114">CD %SystemDrive%\Program Files\Microsoft 10.0\Common7\IDE sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f36b2-114">cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE</span></span>  
  
    2.  <span data-ttu-id="f36b2-115">Spusťte WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="f36b2-115">Run WcfTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="f36b2-116">Stisknutím kombinace kláves CTRL + SHIFT + A a nastavení adresu služby nastavte adresu služby na WcfTestClient.exe http://localhost:56133/Service.xamlx.</span><span class="sxs-lookup"><span data-stu-id="f36b2-116">Set the address of the service on WcfTestClient.exe by pressing CTRL+SHIFT+A and setting the service address to http://localhost:56133/Service.xamlx.</span></span>  
  
5.  <span data-ttu-id="f36b2-117">Provedení operace echo testování služby.</span><span class="sxs-lookup"><span data-stu-id="f36b2-117">Perform the echo operation to test the service.</span></span>  
  
6.  <span data-ttu-id="f36b2-118">Nasazení služby ve službě IIS pomocí DeployToIIS.Bat v příkazovém řádku s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="f36b2-118">Deploy the Service in IIS using DeployToIIS.Bat in a command prompt with administrator privileges.</span></span>  
  
7.  <span data-ttu-id="f36b2-119">Aktualizujte adresu služby v klientovi http://localhost/XAMLActivation/Service.xamlx a testovat službu znovu pomocí WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="f36b2-119">Update the service address in the client to http://localhost/XAMLActivation/Service.xamlx and test the service again using WcfTestClient.exe.</span></span>

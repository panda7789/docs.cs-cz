---
title: Aktivace XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f513b10c84de968d5a18b800037b512aad90399e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-activation"></a><span data-ttu-id="ed9b5-102">Aktivace XAML</span><span class="sxs-lookup"><span data-stu-id="ed9b5-102">XAML Activation</span></span>
<span data-ttu-id="ed9b5-103">Tento příklad ukazuje, jak k hostování deklarativní pracovní postup ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="ed9b5-103">This sample demonstrates how to host a declarative workflow in IIS.</span></span> <span data-ttu-id="ed9b5-104">Ukázka je základní pracovní postup volá `EchoService` má jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="ed9b5-104">The sample is a basic workflow called `EchoService` that has one operation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed9b5-105">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="ed9b5-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ed9b5-106">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ed9b5-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ed9b5-107">Pokud tento adresář neexistuje, přejděte k (stránce pro stažení) Chcete-li stáhnout všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ed9b5-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ed9b5-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ed9b5-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ed9b5-109">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="ed9b5-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ed9b5-110">Otevřete řešení XAMLActivation.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed9b5-110">Open the XAMLActivation.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="ed9b5-111">Sestavte řešení stisknutím **F5**.</span><span class="sxs-lookup"><span data-stu-id="ed9b5-111">Build the solution by pressing **F5**.</span></span>  
  
3.  <span data-ttu-id="ed9b5-112">Spusťte WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="ed9b5-112">Run WcfTestClient.exe.</span></span> <span data-ttu-id="ed9b5-113">Z příkazového řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="ed9b5-113">From a command prompt, type in the following:</span></span>  
  
    1.  <span data-ttu-id="ed9b5-114">CD %SystemDrive%\Program Files\Microsoft 10.0\Common7\IDE sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ed9b5-114">cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE</span></span>  
  
    2.  <span data-ttu-id="ed9b5-115">Spusťte WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="ed9b5-115">Run WcfTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="ed9b5-116">Nastavte adresu služby na WcfTestClient.exe stisknutím kláves CTRL + SHIFT + A a nastavení http://localhost:56133/Service.xamlx adresu služby.</span><span class="sxs-lookup"><span data-stu-id="ed9b5-116">Set the address of the service on WcfTestClient.exe by pressing CTRL+SHIFT+A and setting the service address to http://localhost:56133/Service.xamlx.</span></span>  
  
5.  <span data-ttu-id="ed9b5-117">Provedení operace echo testování služby.</span><span class="sxs-lookup"><span data-stu-id="ed9b5-117">Perform the echo operation to test the service.</span></span>  
  
6.  <span data-ttu-id="ed9b5-118">Nasazení služby ve službě IIS pomocí DeployToIIS.Bat v příkazovém řádku s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="ed9b5-118">Deploy the Service in IIS using DeployToIIS.Bat in a command prompt with administrator privileges.</span></span>  
  
7.  <span data-ttu-id="ed9b5-119">Aktualizujte adresu služby v klientovi http://localhost/XAMLActivation/Service.xamlx a testovat službu znovu pomocí WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="ed9b5-119">Update the service address in the client to http://localhost/XAMLActivation/Service.xamlx and test the service again using WcfTestClient.exe.</span></span>

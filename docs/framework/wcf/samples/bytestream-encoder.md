---
title: Kodér bajtového datového proudu
ms.date: 03/30/2017
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
ms.openlocfilehash: ab9ccf47527dcf7f01f272f09b3b341d30fbd8d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499677"
---
# <a name="bytestream-encoder"></a><span data-ttu-id="63448-102">Kodér bajtového datového proudu</span><span class="sxs-lookup"><span data-stu-id="63448-102">ByteStream Encoder</span></span>
<span data-ttu-id="63448-103">Tento příklad ukazuje, jak vytvořit `ByteStreamHttpBinding`, <xref:System.ServiceModel.Channels.Binding> který předvádí funkce encoder datového proudu bajtů.</span><span class="sxs-lookup"><span data-stu-id="63448-103">This sample demonstrates how to create a `ByteStreamHttpBinding`, a <xref:System.ServiceModel.Channels.Binding> that demonstrates the functionality of the byte stream encoder.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="63448-104">Diskusní</span><span class="sxs-lookup"><span data-stu-id="63448-104">Discussion</span></span>  
 <span data-ttu-id="63448-105">Tento příklad ukazuje, jak vytvořit standard <xref:System.ServiceModel.Channels.Binding> používání prvky standardní vazby <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="63448-105">This sample demonstrates how to create a standard <xref:System.ServiceModel.Channels.Binding> using the standard binding elements <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span> <span data-ttu-id="63448-106">Tento příklad ukazuje způsob použití kodér datového proudu bajtů nahrávání a stahování bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="63448-106">This sample shows how to use the byte stream encoder to upload and download an image.</span></span> <span data-ttu-id="63448-107">Funkce encoder datového proudu bajtů podporuje pouze přenos HTTP a nepodporuje funkce, jako je spolehlivé zasílání zpráv nebo zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="63448-107">The byte stream encoder feature only supports the HTTP transport and it does not support features such as reliable messaging or security.</span></span> <span data-ttu-id="63448-108">Jediným <xref:System.ServiceModel.Channels.MessageVersion> podporována je <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="63448-108">The only <xref:System.ServiceModel.Channels.MessageVersion> supported is <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="63448-109">Pokud používáte této ukázce [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] nebo [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], ujistěte se, že používáte [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="63448-109">If you are running this sample in [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] or [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], ensure that you are running [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with elevated privileges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="63448-110">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="63448-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="63448-111">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="63448-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="63448-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="63448-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="63448-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="63448-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="63448-114">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="63448-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="63448-115">Otevřete soubor ByteStreamHttpBinding.sln v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63448-115">Open the ByteStreamHttpBinding.sln file in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="63448-116">Spusťte novou instanci třídy ByteStreamHttpBindingServer projektu kliknutím pravým tlačítkem na projekt v Průzkumníku řešení a výběrem **ladění**a potom **spustit novou instanci** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="63448-116">Start a new instance of the ByteStreamHttpBindingServer project by right-clicking the project in the Solution Explorer and selecting **Debug**, and then **Start new instance** from the context menu.</span></span>  
  
3.  <span data-ttu-id="63448-117">Spusťte novou instanci třídy ByteStreamHttpBindingClient projektu kliknutím pravým tlačítkem na projekt v Průzkumníku řešení a výběrem **ladění**, **spustit novou instanci** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="63448-117">Start a new instance of the ByteStreamHttpBindingClient project by right-clicking the project in the Solution Explorer and selecting **Debug**, **Start new instance** from the context menu.</span></span>

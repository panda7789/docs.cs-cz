---
title: "Režim kompatibility ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
caps.latest.revision: "25"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 953bc79207b7006977a0eb96e0026767bf05194c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="58f91-102">Režim kompatibility ASP.NET</span><span class="sxs-lookup"><span data-stu-id="58f91-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="58f91-103">Tento příklad ukazuje, jak povolit [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] režimu kompatibility v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58f91-103">This sample demonstrates how to enable [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Compatibility mode in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="58f91-104">Služby spuštěné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] režim kompatibility účast ve plně [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace kanálu a mohl provádět použití [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkce jako je například autorizace soubor nebo adresa URL, stav relace a <xref:System.Web.HttpContext> – třída.</span><span class="sxs-lookup"><span data-stu-id="58f91-104">Services running in [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Compatibility mode participate fully in the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application pipeline and can make use of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="58f91-105"><xref:System.Web.HttpContext> Třída umožňuje přístup k souborů cookie, relací a další [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkce.</span><span class="sxs-lookup"><span data-stu-id="58f91-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] features.</span></span> <span data-ttu-id="58f91-106">Tento režim vyžaduje, aby vazby používají přenos HTTP a samotné služby musí být hostované ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="58f91-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="58f91-107">V této ukázce klienta je konzolová aplikace (spustitelného souboru) a služba je hostovaná v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="58f91-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58f91-108">Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="58f91-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58f91-109">Tato ukázka vyžaduje [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] fond aplikací, aby bylo možné spustit.</span><span class="sxs-lookup"><span data-stu-id="58f91-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="58f91-110">Chcete-li vytvořit nový fond aplikací, nebo upravit výchozí fond aplikací, postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="58f91-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  
>   
>  1.  <span data-ttu-id="58f91-111">Otevřete **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="58f91-111">Open **Control Panel**.</span></span>  <span data-ttu-id="58f91-112">Otevřete **nástroje pro správu** aplet pod **systém a zabezpečení** záhlaví.</span><span class="sxs-lookup"><span data-stu-id="58f91-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="58f91-113">Otevřete **Správce Internetové informační služby (IIS)** aplet.</span><span class="sxs-lookup"><span data-stu-id="58f91-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  
> 2.  <span data-ttu-id="58f91-114">Rozbalte položku ve stromovém zobrazení **připojení** podokně.</span><span class="sxs-lookup"><span data-stu-id="58f91-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="58f91-115">Vyberte **fondy aplikací** uzlu.</span><span class="sxs-lookup"><span data-stu-id="58f91-115">Select the **Application Pools** node.</span></span>  
> 3.  <span data-ttu-id="58f91-116">Nastavit výchozí fond aplikací používat [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (která může způsobit problémy s kompatibilitou s existujícími lokalitami), klikněte pravým tlačítkem myši **DefaultAppPool** položky seznamu a vyberte **základní nastavení...** .</span><span class="sxs-lookup"><span data-stu-id="58f91-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="58f91-117">Nastavte **rozhraní .net Framework verze** rozevírací k **rozhraní .net Framework v4.0.30128** (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="58f91-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  
> 4.  <span data-ttu-id="58f91-118">Chcete-li vytvořit nový fond aplikací, který používá [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (pro zachování kompatibility pro jiné aplikace), klikněte pravým tlačítkem myši **fondy aplikací** uzel a vyberte možnost **přidat fond aplikací...** .</span><span class="sxs-lookup"><span data-stu-id="58f91-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="58f91-119">Název nového fondu aplikací a nastavte **rozhraní .net Framework verze** rozevírací k **rozhraní .net Framework v4.0.30128** (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="58f91-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="58f91-120">Po spuštění instalačního programu kroky níže, klikněte pravým tlačítkem myši **ServiceModelSamples** aplikace a vyberte možnost **spravovat aplikace**, **Upřesnit nastavení...** .</span><span class="sxs-lookup"><span data-stu-id="58f91-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="58f91-121">Nastavte **fond aplikací** na nový fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="58f91-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="58f91-122">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="58f91-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="58f91-123">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="58f91-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="58f91-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="58f91-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="58f91-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="58f91-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="58f91-126">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="58f91-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="58f91-127">`ICalculator` Kontrakt změnila jako `ICalculatorSession` Smlouvy umožňující sadu operací, které mají být provedeny, a zajistit přitom ochranu výsledku spuštěné.</span><span class="sxs-lookup"><span data-stu-id="58f91-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="58f91-128">Služba Udržovat stav, používá funkci, pro každého klienta jako výpočet se říká víc operací služeb.</span><span class="sxs-lookup"><span data-stu-id="58f91-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="58f91-129">Klient může získat aktuální výsledek pomocí volání `Result` a můžete vymazat výsledek, který má nula voláním `Clear`.</span><span class="sxs-lookup"><span data-stu-id="58f91-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="58f91-130">Služba používá [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] relace uložit výsledek pro každou relaci klienta.</span><span class="sxs-lookup"><span data-stu-id="58f91-130">The service uses the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session to store the result for each client session.</span></span> <span data-ttu-id="58f91-131">To umožňuje službě udržet spuštěné výsledek u jednotlivých klientů přes několik volání do služby.</span><span class="sxs-lookup"><span data-stu-id="58f91-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="58f91-132">Stav relace a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] relací jsou velmi různých věcí.</span><span class="sxs-lookup"><span data-stu-id="58f91-132"> session state and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessions are very different things.</span></span>  <span data-ttu-id="58f91-133">Najdete v článku [relace](../../../../docs/framework/wcf/samples/session.md) podrobnosti o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] relací.</span><span class="sxs-lookup"><span data-stu-id="58f91-133">See the [Session](../../../../docs/framework/wcf/samples/session.md) for details on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessions.</span></span>  
  
 <span data-ttu-id="58f91-134">Služba má dokonalou závislost [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] stavu relace a vyžaduje [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] režimu kompatibility, aby správně fungoval.</span><span class="sxs-lookup"><span data-stu-id="58f91-134">The service has an intimate dependency on [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session state and requires [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] compatibility mode to function correctly.</span></span> <span data-ttu-id="58f91-135">Tyto požadavky jsou vyjádřeny deklarativně použitím `AspNetCompatibilityRequirements` atribut.</span><span class="sxs-lookup"><span data-stu-id="58f91-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
```  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```  
  
 <span data-ttu-id="58f91-136">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="58f91-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="58f91-137">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="58f91-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="58f91-138">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="58f91-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="58f91-139">Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58f91-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="58f91-140">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58f91-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="58f91-141">Po vytvoření řešení, spusťte Setup.bat nastavit aplikaci ServiceModelSamples v [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58f91-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="58f91-142">Adresář ServiceModelSamples by se měla zobrazit jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="58f91-142">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="58f91-143">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58f91-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f91-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="58f91-144">See Also</span></span>  
 [<span data-ttu-id="58f91-145">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="58f91-145">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)

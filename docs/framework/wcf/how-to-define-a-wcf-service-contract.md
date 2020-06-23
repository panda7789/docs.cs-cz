---
title: 'Kurz: Definování kontraktu Windows Communication Foundation služby'
description: Naučte se definovat kontrakt služby jako součást série článků, které vám pomůžou začít vytvářet aplikace WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 5cb371da8c7180b8c4cbf5ac11468fbb8e0e13cc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246308"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="95090-103">Kurz: Definování kontraktu Windows Communication Foundation služby</span><span class="sxs-lookup"><span data-stu-id="95090-103">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="95090-104">Tento kurz popisuje prvních pět úloh nutných k vytvoření aplikace Basic Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="95090-104">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="95090-105">Přehled kurzů najdete v tématu [kurz: Začínáme s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="95090-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="95090-106">Při vytváření služby WCF je vaším prvním úkolem Definování kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="95090-106">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="95090-107">Kontrakt služby určuje, které operace služba podporuje.</span><span class="sxs-lookup"><span data-stu-id="95090-107">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="95090-108">Operaci lze představit jako metodu webové služby.</span><span class="sxs-lookup"><span data-stu-id="95090-108">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="95090-109">Kontrakty služby vytvoříte definováním rozhraní C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="95090-109">You create service contracts by defining a C# or Visual Basic interface.</span></span> <span data-ttu-id="95090-110">Rozhraní má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="95090-110">An interface has the following characteristics:</span></span>

- <span data-ttu-id="95090-111">Každá metoda v rozhraní odpovídá konkrétní operaci služby.</span><span class="sxs-lookup"><span data-stu-id="95090-111">Each method in the interface corresponds to a specific service operation.</span></span>
- <span data-ttu-id="95090-112">Pro každé rozhraní je nutné použít <xref:System.ServiceModel.ServiceContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="95090-112">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="95090-113">Pro každou operaci/metodu je nutné použít <xref:System.ServiceModel.OperationContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="95090-113">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

<span data-ttu-id="95090-114">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="95090-114">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="95090-115">Vytvořte projekt **knihovny služby WCF** .</span><span class="sxs-lookup"><span data-stu-id="95090-115">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="95090-116">Definujte rozhraní kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="95090-116">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="95090-117">Vytvoření projektu knihovny služby WCF a definování rozhraní kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="95090-117">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="95090-118">Otevřete Visual Studio jako správce.</span><span class="sxs-lookup"><span data-stu-id="95090-118">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="95090-119">Provedete to tak, že v nabídce **Start** vyberete program Visual Studio a v místní nabídce vyberete **Další**  >  **Spustit jako správce** .</span><span class="sxs-lookup"><span data-stu-id="95090-119">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="95090-120">Vytvořte projekt **knihovny služby WCF** .</span><span class="sxs-lookup"><span data-stu-id="95090-120">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="95090-121">V nabídce **soubor** vyberte možnost **Nový**  >  **projekt**.</span><span class="sxs-lookup"><span data-stu-id="95090-121">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="95090-122">V dialogovém okně **Nový projekt** , na levé straně, rozbalte položku **Visual C#** nebo **Visual Basic**a pak vyberte kategorii **WCF** .</span><span class="sxs-lookup"><span data-stu-id="95090-122">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="95090-123">Visual Studio zobrazí seznam šablon projektů v části Center v okně.</span><span class="sxs-lookup"><span data-stu-id="95090-123">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="95090-124">Vyberte **knihovnu služby WCF**.</span><span class="sxs-lookup"><span data-stu-id="95090-124">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="95090-125">Pokud nevidíte kategorii šablony projektů **WCF** , bude pravděpodobně nutné nainstalovat **Windows Communication Foundation** součást sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="95090-125">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="95090-126">V dialogovém okně **Nový projekt** vyberte odkaz **otevřít instalační program pro Visual Studio** na levé straně.</span><span class="sxs-lookup"><span data-stu-id="95090-126">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="95090-127">Vyberte kartu **jednotlivé součásti** a v kategorii **vývojové aktivity** vyhledejte a vyberte **Windows Communication Foundation** .</span><span class="sxs-lookup"><span data-stu-id="95090-127">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="95090-128">Chcete-li zahájit instalaci komponenty, klikněte na tlačítko **Upravit** .</span><span class="sxs-lookup"><span data-stu-id="95090-128">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="95090-129">V dolní části okna zadejte *GettingStartedLib* pro **název** a *soubor GettingStarted* pro **název řešení**.</span><span class="sxs-lookup"><span data-stu-id="95090-129">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span>

   4. <span data-ttu-id="95090-130">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="95090-130">Select **OK**.</span></span>

      <span data-ttu-id="95090-131">Visual Studio vytvoří projekt, který má tři soubory: *IService1.cs* (nebo *IService1. vb* pro projekt Visual Basic), *Service1.cs* (nebo *Service1. vb* pro Visual Basic projekt) a *App.config*. Visual Studio definuje tyto soubory následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="95090-131">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span>
      - <span data-ttu-id="95090-132">Soubor *IService1* obsahuje výchozí definici kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="95090-132">The *IService1* file contains the default definition of the service contract.</span></span>
      - <span data-ttu-id="95090-133">Soubor *Service1* obsahuje výchozí implementaci kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="95090-133">The *Service1* file contains the default implementation of the service contract.</span></span>
      - <span data-ttu-id="95090-134">*App.config* soubor obsahuje informace o konfiguraci potřebné k načtení výchozí služby pomocí nástroje pro hostování služby Visual Studio WCF.</span><span class="sxs-lookup"><span data-stu-id="95090-134">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="95090-135">Další informace o nástroji pro hostování služby WCF najdete v tématu [Hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="95090-135">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="95090-136">Pokud jste nainstalovali Visual Studio s Visual Basic nastavení vývojářského prostředí, řešení může být skryté.</span><span class="sxs-lookup"><span data-stu-id="95090-136">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="95090-137">Pokud se jedná o tento případ, vyberte **Možnosti** v nabídce **nástroje** a pak v okně Možnosti vyberte **projekty a řešení**  >  **Obecné** . **Options**</span><span class="sxs-lookup"><span data-stu-id="95090-137">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="95090-138">Vyberte možnost **vždy zobrazit řešení**.</span><span class="sxs-lookup"><span data-stu-id="95090-138">Select **Always show solution**.</span></span> <span data-ttu-id="95090-139">Ověřte také, že je vybrána možnost **Uložit nové projekty při vytvoření** .</span><span class="sxs-lookup"><span data-stu-id="95090-139">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="95090-140">Z **Průzkumník řešení**otevřete soubor **IService1.cs** nebo **IService1. vb** a nahraďte jeho kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="95090-140">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
            public interface ICalculator
            {
                [OperationContract]
                double Add(double n1, double n2);
                [OperationContract]
                double Subtract(double n1, double n2);
                [OperationContract]
                double Multiply(double n1, double n2);
                [OperationContract]
                double Divide(double n1, double n2);
            }
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     <span data-ttu-id="95090-141">Tato Smlouva definuje online kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="95090-141">This contract defines an online calculator.</span></span> <span data-ttu-id="95090-142">Všimněte si, že `ICalculator` rozhraní je označeno <xref:System.ServiceModel.ServiceContractAttribute> atributem (zjednodušeno jako `ServiceContract` ).</span><span class="sxs-lookup"><span data-stu-id="95090-142">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="95090-143">Tento atribut definuje obor názvů pro jednoznačnost názvu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="95090-143">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="95090-144">Kód označí každou operaci kalkulačky <xref:System.ServiceModel.OperationContractAttribute> atributem (zjednodušeno jako `OperationContract` ).</span><span class="sxs-lookup"><span data-stu-id="95090-144">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="95090-145">Další kroky</span><span class="sxs-lookup"><span data-stu-id="95090-145">Next steps</span></span>

<span data-ttu-id="95090-146">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="95090-146">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="95090-147">Vytvořte projekt knihovny služby WCF.</span><span class="sxs-lookup"><span data-stu-id="95090-147">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="95090-148">Definujte rozhraní kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="95090-148">Define a service contract interface.</span></span>

<span data-ttu-id="95090-149">Přejděte k dalšímu kurzu, kde se dozvíte, jak implementovat kontrakt služby WCF.</span><span class="sxs-lookup"><span data-stu-id="95090-149">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="95090-150">Kurz: implementace kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="95090-150">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)

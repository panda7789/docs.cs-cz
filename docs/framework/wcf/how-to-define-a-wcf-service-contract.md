---
title: 'Kurz: Definování kontraktu služby Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: a1908339460191fcb81d03d45c56dd57b2cf4c4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228390"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="52e03-102">Kurz: Definování kontraktu služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="52e03-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="52e03-103">Tento kurz popisuje prvních pět úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="52e03-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="52e03-104">Přehled v kurzech, naleznete v tématu [kurzu: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="52e03-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="52e03-105">Při vytváření služeb WCF je první úkol k definování kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="52e03-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="52e03-106">Kontrakt služby specifikuje, jaké operace služba podporuje.</span><span class="sxs-lookup"><span data-stu-id="52e03-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="52e03-107">Operace můžete představit jako metodu webové služby.</span><span class="sxs-lookup"><span data-stu-id="52e03-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="52e03-108">Vytváření kontraktů služby tak, že definujete Vizuálu C# nebo rozhraní jazyka Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="52e03-108">You create service contracts by defining a Visual C# or Visual Basic (VB) interface.</span></span> <span data-ttu-id="52e03-109">Rozhraní má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="52e03-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="52e03-110">Každá metoda v rozhraní odpovídá konkrétní operaci služby.</span><span class="sxs-lookup"><span data-stu-id="52e03-110">Each method in the interface corresponds to a specific service operation.</span></span> 
- <span data-ttu-id="52e03-111">Pro každé rozhraní, musíte použít <xref:System.ServiceModel.ServiceContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="52e03-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="52e03-112">Pro každou operaci/metodu, musíte použít <xref:System.ServiceModel.OperationContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="52e03-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> 

<span data-ttu-id="52e03-113">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="52e03-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="52e03-114">Vytvoření **knihovny služby WCF** projektu.</span><span class="sxs-lookup"><span data-stu-id="52e03-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="52e03-115">Definujte rozhraní kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="52e03-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="52e03-116">Vytvořte projekt knihovny služby WCF a definování rozhraní kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="52e03-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="52e03-117">Otevřít Visual Studio jako správce.</span><span class="sxs-lookup"><span data-stu-id="52e03-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="52e03-118">Pokud chcete udělat, vyberte program sady Visual Studio v **Start** nabídky a pak vyberte **Další** > **spustit jako správce** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="52e03-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="52e03-119">Vytvoření **knihovny služby WCF** projektu.</span><span class="sxs-lookup"><span data-stu-id="52e03-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="52e03-120">Z **souboru** nabídce vyberte možnost **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="52e03-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="52e03-121">V **nový projekt** na levé straně dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **WCF** kategorie.</span><span class="sxs-lookup"><span data-stu-id="52e03-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="52e03-122">Visual Studio zobrazí seznam šablon projektů v části System center okna.</span><span class="sxs-lookup"><span data-stu-id="52e03-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="52e03-123">Vyberte **knihovny služby WCF**.</span><span class="sxs-lookup"><span data-stu-id="52e03-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="52e03-124">Pokud se nezobrazí **WCF** kategorii šablony projektu, budete muset nainstalovat **Windows Communication Foundation** komponentu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="52e03-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="52e03-125">V **nový projekt** dialogové okno, vyberte **otevřít instalační program Visual Studio** odkazu na levé straně.</span><span class="sxs-lookup"><span data-stu-id="52e03-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="52e03-126">Vyberte **jednotlivé komponenty** kartu a potom najděte a vyberte **Windows Communication Foundation** pod **vývojových aktivit** kategorie.</span><span class="sxs-lookup"><span data-stu-id="52e03-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="52e03-127">Zvolte **změnit** zahájíte instalaci komponenty.</span><span class="sxs-lookup"><span data-stu-id="52e03-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="52e03-128">V dolní části okna, zadejte *GettingStartedLib* pro **název** a *GettingStarted* pro **název řešení**.</span><span class="sxs-lookup"><span data-stu-id="52e03-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span> 

   4. <span data-ttu-id="52e03-129">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="52e03-129">Select **OK**.</span></span>

      <span data-ttu-id="52e03-130">Visual Studio vytvoří projekt, který má tři soubory: *IService1.cs* (nebo *IService1.vb* pro projekt jazyka Visual Basic), *Service1.cs* (nebo *Service1.vb* pro projekt jazyka Visual Basic), a  *App.config*. Visual Studio definuje tyto soubory následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="52e03-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span> 
      - <span data-ttu-id="52e03-131">*IService1* soubor obsahuje výchozí definici kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="52e03-131">The *IService1* file contains the default definition of the service contract.</span></span> 
      - <span data-ttu-id="52e03-132">*Service1* soubor obsahuje výchozí implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="52e03-132">The *Service1* file contains the default implementation of the service contract.</span></span> 
      - <span data-ttu-id="52e03-133">*App.config* soubor obsahuje informace o konfiguraci potřebné k načtení výchozí služby pomocí nástroje Visual Studio WCF služby hostitele.</span><span class="sxs-lookup"><span data-stu-id="52e03-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="52e03-134">Další informace o nástroji pro hostitele služby WCF najdete v tématu [hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="52e03-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="52e03-135">Pokud jste nainstalovali aplikaci Visual Studio pomocí nastavení prostředí pro vývojáře jazyka Visual Basic, může být skrytá řešení.</span><span class="sxs-lookup"><span data-stu-id="52e03-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="52e03-136">Pokud je to tento případ, vyberte **možnosti** z **nástroje** nabídce pak vyberte **projekty a řešení** > **Obecné** v **možnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="52e03-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="52e03-137">Vyberte **vždy zobrazit řešení**.</span><span class="sxs-lookup"><span data-stu-id="52e03-137">Select **Always show solution**.</span></span> <span data-ttu-id="52e03-138">Kromě toho ověřte, že **uložit nové projekty při vytvoření** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="52e03-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="52e03-139">Z **Průzkumníka řešení**, otevřete **IService1.cs** nebo **IService1.vb** souboru a jeho kódu nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="52e03-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="52e03-140">Tento kontrakt definuje online kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="52e03-140">This contract defines an online calculator.</span></span> <span data-ttu-id="52e03-141">Všimněte si, že `ICalculator` rozhraní je označeno příznakem s <xref:System.ServiceModel.ServiceContractAttribute> atribut (zjednodušené jako `ServiceContract`).</span><span class="sxs-lookup"><span data-stu-id="52e03-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="52e03-142">Tento atribut definuje obor názvů k rozlišení názvu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="52e03-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="52e03-143">Kód označuje každá operace kalkulačky s <xref:System.ServiceModel.OperationContractAttribute> atribut (zjednodušené jako `OperationContract`).</span><span class="sxs-lookup"><span data-stu-id="52e03-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="52e03-144">Další kroky</span><span class="sxs-lookup"><span data-stu-id="52e03-144">Next steps</span></span>

<span data-ttu-id="52e03-145">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="52e03-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="52e03-146">Vytvořte projekt knihovny služby WCF.</span><span class="sxs-lookup"><span data-stu-id="52e03-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="52e03-147">Definujte rozhraní kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="52e03-147">Define a service contract interface.</span></span>

<span data-ttu-id="52e03-148">Přejděte k dalšímu kurzu se naučíte implementace kontraktu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="52e03-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="52e03-149">Kurz: Implementace kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="52e03-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)

---
title: 'Postupy: Definování kontraktu služby WCF'
ms.date: 09/14/2018
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 4f85a51c47eb045d1d2f0111cb217199c9acf0d7
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009005"
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="b0fe7-102">Postupy: Definování kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="b0fe7-102">How to: Define a Windows Communication Foundation Service Contract</span></span>

<span data-ttu-id="b0fe7-103">Toto je první z šesti úkolů, muset vytvořit základní aplikaci Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b0fe7-103">This is the first of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="b0fe7-104">Přehled všech šesti úkoly, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

 <span data-ttu-id="b0fe7-105">Při vytváření služby WCF, je první úkol k definování kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-105">When creating a WCF service, the first task is to define a service contract.</span></span> <span data-ttu-id="b0fe7-106">Kontrakt služby specifikuje, jaké operace služba podporuje.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="b0fe7-107">Operace můžete představit jako metodu webové služby.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="b0fe7-108">Kontrakty se vytvoří definováním rozhraní C++, C# nebo Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="b0fe7-108">Contracts are created by defining a C++, C#, or Visual Basic (VB) interface.</span></span> <span data-ttu-id="b0fe7-109">Každá metoda v rozhraní odpovídá konkrétní operaci služby.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-109">Each method in the interface corresponds to a specific service operation.</span></span> <span data-ttu-id="b0fe7-110">Každé rozhraní musí mít <xref:System.ServiceModel.ServiceContractAttribute> použit a každá operace musí mít <xref:System.ServiceModel.OperationContractAttribute> byt aplikovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-110">Each interface must have the <xref:System.ServiceModel.ServiceContractAttribute> applied to it and each operation must have the <xref:System.ServiceModel.OperationContractAttribute> attribute applied to it.</span></span> <span data-ttu-id="b0fe7-111">Pokud metoda v rozhraní, který má <xref:System.ServiceModel.ServiceContractAttribute> atribut nemá <xref:System.ServiceModel.OperationContractAttribute> atribut, taková metoda se nevystaví službou.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-111">If a method within an interface that has the <xref:System.ServiceModel.ServiceContractAttribute> attribute does not have the <xref:System.ServiceModel.OperationContractAttribute> attribute, that method is not exposed by the service.</span></span>

 <span data-ttu-id="b0fe7-112">Kód použitý pro tuto úlohu je najdete v příkladu za postupem.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-112">The code used for this task is provided in the example following the procedure.</span></span>

## <a name="define-a-service-contract"></a><span data-ttu-id="b0fe7-113">Definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="b0fe7-113">Define a service contract</span></span>

1. <span data-ttu-id="b0fe7-114">Otevřít Visual Studio jako správce kliknutím pravým tlačítkem myši v programu **Start** nabídky a vyberete **Další** > **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-114">Open Visual Studio as an administrator by right-clicking the program in the **Start** menu and selecting **More** > **Run as administrator**.</span></span>

2. <span data-ttu-id="b0fe7-115">Vytvořte projekt knihovny služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-115">Create a WCF Service Library project.</span></span>

   1. <span data-ttu-id="b0fe7-116">Z **souboru** nabídce vyberte možnost **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-116">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="b0fe7-117">V **nový projekt** na levé straně dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **WCF** kategorie.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-117">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="b0fe7-118">V části System center dialogového okna se zobrazí seznam šablon projektů.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-118">A list of project templates is displayed in the center section of the dialog.</span></span> <span data-ttu-id="b0fe7-119">Vyberte **knihovny služby WCF**.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-119">Select **WCF Service Library**.</span></span>

   3. <span data-ttu-id="b0fe7-120">Zadejte `GettingStartedLib` v **název** textového pole a `GettingStarted` v **název řešení** textového pole v dolní části dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-120">Enter `GettingStartedLib` in the **Name** textbox and `GettingStarted` in the **Solution name** textbox at the bottom of the dialog.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b0fe7-121">Pokud se nezobrazí **WCF** kategorii šablony projektu, budete muset nainstalovat **Windows Communication Foundation** komponentu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-121">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="b0fe7-122">V **nový projekt** dialogovém okně klikněte na odkaz, který uvádí, že **otevřít instalační program Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-122">In the **New Project** dialog box, click the link that says **Open Visual Studio Installer**.</span></span> <span data-ttu-id="b0fe7-123">Vyberte **jednotlivé komponenty** kartu a potom najděte a vyberte **Windows Communication Foundation** pod **vývojových aktivit** kategorie.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-123">Select the **Individual Components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="b0fe7-124">Zvolte **změnit** zahájíte instalaci komponenty.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-124">Choose **Modify** to begin installing the component.</span></span>

   <span data-ttu-id="b0fe7-125">Visual Studio vytvoří projekt, který obsahuje 3 soubory: IService1.cs (nebo IService1.vb) Service1.cs (nebo Service1.vb) a souboru App.config. Soubor IService1 obsahuje výchozí smlouvy o poskytování služeb.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-125">Visual Studio creates the project, which contains 3 files: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb), and App.config. The IService1 file contains a default service contract.</span></span> <span data-ttu-id="b0fe7-126">Soubor Service1 obsahuje výchozí implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-126">The Service1 file contains a default implementation of the service contract.</span></span> <span data-ttu-id="b0fe7-127">Soubor App.config obsahuje konfigurace, které jsou potřebné k načtení výchozí službu s Visual Studio hostitel služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-127">The App.config file contains configuration needed to load the default service with the Visual Studio WCF Service Host.</span></span> <span data-ttu-id="b0fe7-128">Další informace o nástroji pro hostitele služby WCF najdete v tématu [hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="b0fe7-128">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span></span>

3. <span data-ttu-id="b0fe7-129">Otevřete soubor IService1.cs nebo IService1.vb a odstranění kódu v rámci deklarace oboru názvů, byste museli opustit deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-129">Open the IService1.cs or IService1.vb file and delete the code within the namespace declaration, leaving the namespace declaration.</span></span> <span data-ttu-id="b0fe7-130">Uvnitř oboru názvů deklarace definujte nové rozhraní s názvem `ICalculator` jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-130">Inside the namespace declaration define a new interface called `ICalculator` as shown in the code below.</span></span>

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

     <span data-ttu-id="b0fe7-131">Tento kontrakt definuje online kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-131">This contract defines an online calculator.</span></span> <span data-ttu-id="b0fe7-132">Všimněte si, že `ICalculator` rozhraní je označeno příznakem s <xref:System.ServiceModel.ServiceContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-132">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="b0fe7-133">Tento atribut definuje obor názvů, který se používá k rozlišení názvu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-133">This attribute defines a namespace that is used to disambiguate the contract name.</span></span> <span data-ttu-id="b0fe7-134">Každá operace kalkulačky je označená pomocí <xref:System.ServiceModel.OperationContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="b0fe7-134">Each calculator operation is marked with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b0fe7-135">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b0fe7-135">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0fe7-136">Postupy: implementace kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="b0fe7-136">How to: Implement a service contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

## <a name="see-also"></a><span data-ttu-id="b0fe7-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0fe7-137">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="b0fe7-138">Postupy: Implementace kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="b0fe7-138">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="b0fe7-139">Začínáme</span><span class="sxs-lookup"><span data-stu-id="b0fe7-139">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="b0fe7-140">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="b0fe7-140">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
---
title: 'Postupy: Definování kontraktu služby WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 5e8abbf8c5f9b0696d90ccbee94c5d8f4dd8b1ec
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="38e48-102">Postupy: Definování kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="38e48-102">How to: Define a Windows Communication Foundation Service Contract</span></span>
<span data-ttu-id="38e48-103">Toto je první šesti úloh, které jsou potřebné pro vytvoření základní aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="38e48-103">This is the first of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="38e48-104">Přehled všech šest úloh najdete v tématu [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="38e48-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="38e48-105">Při vytváření služby WCF, první úlohou je definování kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="38e48-105">When creating a WCF service, the first task is to define a service contract.</span></span> <span data-ttu-id="38e48-106">Kontrakt služby specifikuje, jaké operace služby podporuje.</span><span class="sxs-lookup"><span data-stu-id="38e48-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="38e48-107">Operace můžete představit jako metodu webové služby.</span><span class="sxs-lookup"><span data-stu-id="38e48-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="38e48-108">Kontrakty se vytvoří definováním rozhraní C++, C# nebo Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="38e48-108">Contracts are created by defining a C++, C#, or Visual Basic (VB) interface.</span></span> <span data-ttu-id="38e48-109">Každá metoda v rozhraní odpovídá konkrétní operaci služby.</span><span class="sxs-lookup"><span data-stu-id="38e48-109">Each method in the interface corresponds to a specific service operation.</span></span> <span data-ttu-id="38e48-110">Každé rozhraní musí mít <xref:System.ServiceModel.ServiceContractAttribute> použije na ni a každou operace musí mít <xref:System.ServiceModel.OperationContractAttribute> byt aplikovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="38e48-110">Each interface must have the <xref:System.ServiceModel.ServiceContractAttribute> applied to it and each operation must have the <xref:System.ServiceModel.OperationContractAttribute> attribute applied to it.</span></span> <span data-ttu-id="38e48-111">Pokud metoda v rozhraní, které má <xref:System.ServiceModel.ServiceContractAttribute> atribut nemá <xref:System.ServiceModel.OperationContractAttribute> atribut, taková metoda se nevystaví službou.</span><span class="sxs-lookup"><span data-stu-id="38e48-111">If a method within an interface that has the <xref:System.ServiceModel.ServiceContractAttribute> attribute does not have the <xref:System.ServiceModel.OperationContractAttribute> attribute, that method is not exposed by the service.</span></span>  
  
 <span data-ttu-id="38e48-112">Kód použitý pro tuto úlohu je najdete v příkladu za postupem.</span><span class="sxs-lookup"><span data-stu-id="38e48-112">The code used for this task is provided in the example following the procedure.</span></span>  
  
### <a name="to-define-a-service-contract"></a><span data-ttu-id="38e48-113">K definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="38e48-113">To define a service contract</span></span>  
  
1.  <span data-ttu-id="38e48-114">Otevřete [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] jako správce program pravým tlačítkem myši **spustit** nabídky a výběrem **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="38e48-114">Open  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] as an administrator by right-clicking the program in the **Start** menu and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="38e48-115">Kliknutím na vytvořit projekt knihovny služby WCF **soubor** nabídky a výběrem **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="38e48-115">Create a WCF Service Library project by clicking the **File** menu and selecting **New**, **Project**.</span></span> <span data-ttu-id="38e48-116">V **nový projekt** dialogu na levé straně dialogového okna rozbalte **Visual C#** pro projekt C# nebo **jiné jazyky** a potom **jazykaVisualBasic** pro projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="38e48-116">In the **New Project** dialog, on the left-hand side of the dialog expand **Visual C#** for a C# project or **Other Languages** and then **Visual Basic** for a Visual Basic project.</span></span> <span data-ttu-id="38e48-117">V části jazyk vybraný vyberte **WCF** a zobrazí se seznam šablon projektu na části center dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="38e48-117">Under the language selected select **WCF** and a list of project templates will be displayed on the center section of the dialog.</span></span> <span data-ttu-id="38e48-118">Vyberte **knihovny služby WCF**a typ `GettingStartedLib` v **název** textové pole a `GettingStarted` v **název řešení** textového pole v dolní části dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="38e48-118">Select **WCF Service Library**, and type `GettingStartedLib` in the **Name** textbox and `GettingStarted` in the **Solution name** textbox at the bottom of the dialog.</span></span>  
  
3.  <span data-ttu-id="38e48-119">Visual Studio vytvoří projekt, který obsahuje soubory 3: IService1.cs (nebo IService1.vb) Service1.cs (nebo Service1.vb) a souboru App.config.  Soubor IService1 obsahuje výchozí smlouvy o poskytování služeb.</span><span class="sxs-lookup"><span data-stu-id="38e48-119">Visual Studio will create the project which contains 3 files: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb), and App.config.  The IService1 file contains a default service contract.</span></span>  <span data-ttu-id="38e48-120">Soubor Service1 obsahuje výchozí implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="38e48-120">The Service1 file contains a default implementation of the service contract.</span></span> <span data-ttu-id="38e48-121">Soubor App.config obsahuje konfiguraci potřebné k načtení výchozí služba s Visual Studio hostitel služby WCF.</span><span class="sxs-lookup"><span data-stu-id="38e48-121">The App.config file contains configuration needed to load the default service with the Visual Studio WCF Service Host.</span></span> <span data-ttu-id="38e48-122">Další informace o nástroji pro hostitele služeb WCF najdete v tématu [hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="38e48-122">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span></span>  
  
4.  <span data-ttu-id="38e48-123">Otevřete soubor IService1.cs nebo IService1.vb a odstraňte kód v deklaraci oboru názvů ponechat deklaraci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="38e48-123">Open the IService1.cs or IService1.vb file and delete the code within the namespace declaration leaving the namespace declaration.</span></span> <span data-ttu-id="38e48-124">V oboru názvů deklarace definujte nové rozhraní nazývá `ICalculator` jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="38e48-124">Inside the namespace declaration define a new interface called `ICalculator` as shown in the code below.</span></span>  
  
    ```  
    // IService.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
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
  
    ```  
    ‘IService.vb  
    Imports System  
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
  
     <span data-ttu-id="38e48-125">Tento kontrakt definuje online kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="38e48-125">This contract defines an online calculator.</span></span> <span data-ttu-id="38e48-126">Upozornění `ICalculator` rozhraní je označené jako <xref:System.ServiceModel.ServiceContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="38e48-126">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="38e48-127">Tento atribut definuje obor názvů, který se používá k rozlišení názvu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="38e48-127">This attribute defines a namespace that is used to disambiguate the contract name.</span></span> <span data-ttu-id="38e48-128">Každé operace kalkulačky je označené jako <xref:System.ServiceModel.OperationContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="38e48-128">Each calculator operation is marked with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="38e48-129">Při používání atributů k anotaci rozhraním, člen nebo třídy, můžete vložit část "Atribut" od názvu atributu.</span><span class="sxs-lookup"><span data-stu-id="38e48-129">When using attributes to annotate an interface, member, or class, you can drop the "Attribute" part from the attribute name.</span></span> <span data-ttu-id="38e48-130">Proto <xref:System.ServiceModel.ServiceContractAttribute> stane `[ServiceContract]` v jazyce C# nebo `<ServiceContract>` v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="38e48-130">So <xref:System.ServiceModel.ServiceContractAttribute> becomes `[ServiceContract]` in C#, or `<ServiceContract>` in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e48-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="38e48-131">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="38e48-132">Postupy: Implementace kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="38e48-132">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="38e48-133">Začínáme</span><span class="sxs-lookup"><span data-stu-id="38e48-133">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="38e48-134">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="38e48-134">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)

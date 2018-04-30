---
title: 'Postupy: vytvoření služby pracovního postupu, který využívá existující smlouvy služby'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c7c28d8c2edbda5a42a290786b0ff40e3ab6dd5b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="862e7-102">Postupy: vytvoření služby pracovního postupu, který využívá existující smlouvy služby</span><span class="sxs-lookup"><span data-stu-id="862e7-102">How to: Create a workflow service that consumes an existing service contract</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="862e7-103"> Funkce lepší integrace mezi webové služby a pracovní postupy ve formě vývoj kontrakt první pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="862e7-103"> features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="862e7-104">Nástroj pro vývoj kontrakt první pracovního postupu můžete navrhnout první kontrakt v kódu.</span><span class="sxs-lookup"><span data-stu-id="862e7-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="862e7-105">Nástroj potom automaticky generuje šablonu aktivit v sadě nástrojů pro operace v kontraktu.</span><span class="sxs-lookup"><span data-stu-id="862e7-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="862e7-106">Toto téma obsahuje podrobné pokyny k vytvoření pracovního postupu první kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="862e7-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="862e7-107">Další informace o vývoj pracovního postupu první kontraktu služby najdete v tématu [kontrakt první pracovní postup služby vývoj](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="862e7-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="862e7-108">Vytvoření projektu pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="862e7-108">Creating the workflow project</span></span>  
  
1.  <span data-ttu-id="862e7-109">V sadě Visual Studio, vyberte **soubor**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="862e7-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="862e7-110">Vyberte **WCF** pod uzlem **C#** uzel v **šablony** stromu a vyberte **aplikace služby pracovního postupu WCF** šablony.</span><span class="sxs-lookup"><span data-stu-id="862e7-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2.  <span data-ttu-id="862e7-111">Název nového projektu `ContractFirst` a klikněte na tlačítko **Ok**.</span><span class="sxs-lookup"><span data-stu-id="862e7-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="862e7-112">Vytvoření kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="862e7-112">Creating the service contract</span></span>  
  
1.  <span data-ttu-id="862e7-113">Klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a vyberte **přidat**, **novou položku...** .</span><span class="sxs-lookup"><span data-stu-id="862e7-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="862e7-114">Vyberte **kód** uzlu na levé straně a **třída** šablony na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="862e7-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="862e7-115">Pojmenujte novou třídu `IBookService` a klikněte na tlačítko **Ok**.</span><span class="sxs-lookup"><span data-stu-id="862e7-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2.  <span data-ttu-id="862e7-116">V horní části okna kód, který se zobrazí, přidejte příkaz Using k `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="862e7-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  <span data-ttu-id="862e7-117">Definice třídy ukázka změňte na následující definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="862e7-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  <span data-ttu-id="862e7-118">Sestavení projektu stisknutím **Ctrl + Shift + B**.</span><span class="sxs-lookup"><span data-stu-id="862e7-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="862e7-119">Import kontrakt služby</span><span class="sxs-lookup"><span data-stu-id="862e7-119">Importing the service contract</span></span>  
  
1.  <span data-ttu-id="862e7-120">Klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a vyberte **kontrakt služby Import**.</span><span class="sxs-lookup"><span data-stu-id="862e7-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="862e7-121">V části  **\<aktuální projekt >** otevřete všech podřízených uzlů a vyberte **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="862e7-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="862e7-122">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="862e7-122">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="862e7-123">Otevře se dialogové okno, které výstrahy upozorňující, že se operace dokončila úspěšně a že generované aktivity se zobrazí v panelu nástrojů po sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="862e7-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="862e7-124">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="862e7-124">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="862e7-125">Sestavení projektu stisknutím **Ctrl + Shift + B**tak, aby importované aktivity se zobrazí v panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="862e7-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4.  <span data-ttu-id="862e7-126">V **Průzkumníku**, otevřete Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="862e7-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="862e7-127">Pracovní postup služby se zobrazí v návrháři.</span><span class="sxs-lookup"><span data-stu-id="862e7-127">The workflow service will appear in the designer.</span></span>  
  
5.  <span data-ttu-id="862e7-128">Vyberte **pořadí** aktivity.</span><span class="sxs-lookup"><span data-stu-id="862e7-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="862e7-129">V okně vlastností klikněte **...**</span><span class="sxs-lookup"><span data-stu-id="862e7-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="862e7-130">tlačítko v **ImplementedContract** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="862e7-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="862e7-131">V **Editor kolekce typ** okno, které se zobrazí, klikněte na tlačítko **typ** rozevíracího seznamu a vyberte **Procházet pro typy...**</span><span class="sxs-lookup"><span data-stu-id="862e7-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="862e7-132">položka.</span><span class="sxs-lookup"><span data-stu-id="862e7-132">entry.</span></span> <span data-ttu-id="862e7-133">V **Procházet a vyberte .net zadejte** dialogové okno, v části  **\<aktuální projekt >** otevřete všech podřízených uzlů a vyberte **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="862e7-133">In the **Browse and Select a .Net Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="862e7-134">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="862e7-134">Click **OK**.</span></span> <span data-ttu-id="862e7-135">V **Editor kolekce typ** dialogové okno, klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="862e7-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6.  <span data-ttu-id="862e7-136">Vyberte a odstraňte **ReceiveRequest** a **SendResponse** aktivity.</span><span class="sxs-lookup"><span data-stu-id="862e7-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7.  <span data-ttu-id="862e7-137">Ze sady nástrojů, přetáhněte **Buy_ReceiveAndSendReply** a **Checkout_Receive** aktivity na **sekvenční služby** aktivity.</span><span class="sxs-lookup"><span data-stu-id="862e7-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>

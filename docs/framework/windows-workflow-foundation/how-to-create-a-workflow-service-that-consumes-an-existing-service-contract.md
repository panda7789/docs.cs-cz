---
title: 'Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 6d7fa8c9faa84efc84243387cd27aa264f6155eb
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989615"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="64e85-102">Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby</span><span class="sxs-lookup"><span data-stu-id="64e85-102">How to: Create a workflow service that consumes an existing service contract</span></span>
<span data-ttu-id="64e85-103">.NET Framework 4,5 nabízí lepší integraci mezi webovými službami a pracovními postupy ve formě vývoje pracovního postupu prvního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="64e85-103">.NET Framework 4.5 features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="64e85-104">Nástroj pro vývoj pracovního postupu prvního kontraktu vám umožní navrhnout kontrakt v kódu jako první.</span><span class="sxs-lookup"><span data-stu-id="64e85-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="64e85-105">Nástroj pak na panelu nástrojů automaticky vygeneruje šablonu aktivity pro operace ve smlouvě.</span><span class="sxs-lookup"><span data-stu-id="64e85-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64e85-106">V tomto tématu najdete podrobné pokyny k vytvoření služby pracovního postupu pro první kontrakt.</span><span class="sxs-lookup"><span data-stu-id="64e85-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="64e85-107">Další informace o vývoji služeb pracovního postupu prvního kontraktu najdete v tématu věnovaném [vývoji prvního pracovního postupu služby](contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="64e85-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="64e85-108">Vytváření projektu pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="64e85-108">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="64e85-109">V aplikaci Visual Studio zvolte **soubor**, **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="64e85-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="64e85-110">V **C#** uzlu stromu **šablon** vyberte uzel **WCF** a vyberte šablonu **aplikace služby pracovního postupu WCF** .</span><span class="sxs-lookup"><span data-stu-id="64e85-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="64e85-111">Pojmenujte nový `ContractFirst` projekt a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="64e85-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="64e85-112">Vytváření kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="64e85-112">Creating the service contract</span></span>  
  
1. <span data-ttu-id="64e85-113">Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte **Přidat**, **Nová položka.** .</span><span class="sxs-lookup"><span data-stu-id="64e85-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="64e85-114">Vyberte uzel **kódu** na levé straně a šablonu **třídy** na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="64e85-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="64e85-115">Pojmenujte novou `IBookService` třídu a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="64e85-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="64e85-116">V horní části okna kódu, které se zobrazí, přidejte příkaz using do `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="64e85-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="64e85-117">Změňte definici ukázkové třídy na následující definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64e85-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. <span data-ttu-id="64e85-118">Sestavte projekt stisknutím **kombinace kláves CTRL + SHIFT + B**.</span><span class="sxs-lookup"><span data-stu-id="64e85-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="64e85-119">Import kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="64e85-119">Importing the service contract</span></span>  
  
1. <span data-ttu-id="64e85-120">Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte **importovat kontrakt služby**.</span><span class="sxs-lookup"><span data-stu-id="64e85-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="64e85-121">V části  **\<aktuální > projektu**otevřete všechny dílčí uzly a vyberte **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="64e85-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="64e85-122">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="64e85-122">Click **OK**.</span></span>  
  
2. <span data-ttu-id="64e85-123">Otevře se dialogové okno s upozorněním, že operace byla úspěšně dokončena a že generované aktivity budou zobrazeny v sadě nástrojů po sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="64e85-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="64e85-124">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="64e85-124">Click **OK**.</span></span>  
  
3. <span data-ttu-id="64e85-125">Sestavte projekt stisknutím **kombinace kláves CTRL + SHIFT + B**, aby se importované aktivity zobrazily v sadě nástrojů.</span><span class="sxs-lookup"><span data-stu-id="64e85-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="64e85-126">V **Průzkumník řešení**otevřete Service1. xamlx.</span><span class="sxs-lookup"><span data-stu-id="64e85-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="64e85-127">Služba pracovního postupu se zobrazí v návrháři.</span><span class="sxs-lookup"><span data-stu-id="64e85-127">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="64e85-128">Vyberte aktivitu **sekvence** .</span><span class="sxs-lookup"><span data-stu-id="64e85-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="64e85-129">V okno Vlastnosti klikněte na **...**</span><span class="sxs-lookup"><span data-stu-id="64e85-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="64e85-130">na tlačítko vlastnosti **implementedContract** .</span><span class="sxs-lookup"><span data-stu-id="64e85-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="64e85-131">V okně **editoru kolekce typů** , které se zobrazí, klikněte na rozevírací seznam **typ** a vyberte možnost **Vyhledat typy...**</span><span class="sxs-lookup"><span data-stu-id="64e85-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="64e85-132">uvedení.</span><span class="sxs-lookup"><span data-stu-id="64e85-132">entry.</span></span> <span data-ttu-id="64e85-133">V dialogovém okně **Procházet a vybrat typ .NET** v části  **\<aktuální projekt >** otevřete všechny dílčí uzly a vyberte **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="64e85-133">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="64e85-134">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="64e85-134">Click **OK**.</span></span> <span data-ttu-id="64e85-135">V dialogu **Editor kolekcí typů** klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="64e85-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="64e85-136">Vyberte a odstraňte aktivity **ReceiveRequest** a **SendResponse** .</span><span class="sxs-lookup"><span data-stu-id="64e85-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="64e85-137">Z panelu nástrojů přetáhněte aktivitu **Buy_ReceiveAndSendReply** a **Checkout_Receive** na aktivitu **sekvenční služby** .</span><span class="sxs-lookup"><span data-stu-id="64e85-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>

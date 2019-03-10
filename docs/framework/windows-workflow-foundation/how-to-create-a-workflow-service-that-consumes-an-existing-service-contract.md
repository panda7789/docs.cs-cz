---
title: 'Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 57babf216821665613da053f972ff25488418b7d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705061"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="481d6-102">Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby</span><span class="sxs-lookup"><span data-stu-id="481d6-102">How to: Create a workflow service that consumes an existing service contract</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] <span data-ttu-id="481d6-103">Funkce lepší integrace mezi službami webové a pracovní postupy ve formuláři stavící do pracovního postupu vývoje.</span><span class="sxs-lookup"><span data-stu-id="481d6-103">features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="481d6-104">Pracovní postup kontraktem vývojový nástroj umožňuje navrhovat smlouvy v kódu.</span><span class="sxs-lookup"><span data-stu-id="481d6-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="481d6-105">Nástroj potom automaticky vygeneruje šablonu aktivit v sadě nástrojů pro operace v kontraktu.</span><span class="sxs-lookup"><span data-stu-id="481d6-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="481d6-106">Toto téma obsahuje podrobné pokyny k vytváření služby stavící do pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="481d6-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="481d6-107">Další informace o vývoj služby stavící do pracovního postupu najdete v tématu [nasazení služby pracovního postupu prvního kontraktu](contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="481d6-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="481d6-108">Vytvoření projektu pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="481d6-108">Creating the workflow project</span></span>  
  
1.  <span data-ttu-id="481d6-109">V sadě Visual Studio, vyberte **souboru**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="481d6-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="481d6-110">Vyberte **WCF** pod uzlem **C#** uzlu **šablony** stromu a vyberte **aplikace služeb pracovního postupu WCF** Šablona.</span><span class="sxs-lookup"><span data-stu-id="481d6-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2.  <span data-ttu-id="481d6-111">Název nového projektu `ContractFirst` a klikněte na tlačítko **Ok**.</span><span class="sxs-lookup"><span data-stu-id="481d6-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="481d6-112">Vytvoření kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="481d6-112">Creating the service contract</span></span>  
  
1.  <span data-ttu-id="481d6-113">Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **přidat**, **novou položku...** .</span><span class="sxs-lookup"><span data-stu-id="481d6-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="481d6-114">Vyberte **kód** uzlu na levé straně a **třídy** šablon na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="481d6-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="481d6-115">Pojmenujte novou třídu `IBookService` a klikněte na tlačítko **Ok**.</span><span class="sxs-lookup"><span data-stu-id="481d6-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2.  <span data-ttu-id="481d6-116">V horní části okna kódu, který se zobrazí, přidejte příkaz Using do `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="481d6-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  <span data-ttu-id="481d6-117">Ukázková definice třídy změňte na následující definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="481d6-117">Change the sample class definition to the following interface definition.</span></span>  
  
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
  
4.  <span data-ttu-id="481d6-118">Sestavte projekt stisknutím kombinace kláves **Ctrl + Shift + B**.</span><span class="sxs-lookup"><span data-stu-id="481d6-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="481d6-119">Importuje se kontrakt služby</span><span class="sxs-lookup"><span data-stu-id="481d6-119">Importing the service contract</span></span>  
  
1.  <span data-ttu-id="481d6-120">Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **importovat kontrakt služby**.</span><span class="sxs-lookup"><span data-stu-id="481d6-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="481d6-121">V části  **\<aktuální projekt >**, otevřete všechny dílčí uzlů a vyberte **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="481d6-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="481d6-122">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="481d6-122">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="481d6-123">Otevře se dialogové okno, upozorní vás, operace byla úspěšně dokončena a že generované aktivity se zobrazí na panelu nástrojů po sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="481d6-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="481d6-124">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="481d6-124">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="481d6-125">Sestavte projekt stisknutím kombinace kláves **Ctrl + Shift + B**tak, aby importovaná aktivity se zobrazí na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="481d6-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4.  <span data-ttu-id="481d6-126">V **Průzkumníka řešení**, otevřete Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="481d6-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="481d6-127">Služba pracovního postupu se zobrazí v návrháři.</span><span class="sxs-lookup"><span data-stu-id="481d6-127">The workflow service will appear in the designer.</span></span>  
  
5.  <span data-ttu-id="481d6-128">Vyberte **pořadí** aktivity.</span><span class="sxs-lookup"><span data-stu-id="481d6-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="481d6-129">V okně Vlastnosti klikněte na tlačítko **...**</span><span class="sxs-lookup"><span data-stu-id="481d6-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="481d6-130">tlačítko **ImplementedContract** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="481d6-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="481d6-131">V **Editor typu kolekce** okno, které se zobrazí, klikněte **typ** rozevíracím seznamu a vyberte **vyhledat typy...**</span><span class="sxs-lookup"><span data-stu-id="481d6-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="481d6-132">položka.</span><span class="sxs-lookup"><span data-stu-id="481d6-132">entry.</span></span> <span data-ttu-id="481d6-133">V **Procházet a vyberte .net typ** dialogového okna, v části  **\<aktuální projekt >**, otevřete všechny dílčí uzlů a vyberte **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="481d6-133">In the **Browse and Select a .Net Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="481d6-134">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="481d6-134">Click **OK**.</span></span> <span data-ttu-id="481d6-135">V **Editor typu kolekce** dialogového okna, klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="481d6-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6.  <span data-ttu-id="481d6-136">Vyberte a odstraňte **ReceiveRequest** a **SendResponse** aktivity.</span><span class="sxs-lookup"><span data-stu-id="481d6-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7.  <span data-ttu-id="481d6-137">Z panelu nástrojů přetáhněte **Buy_ReceiveAndSendReply** a **Checkout_Receive** aktivity do **sekvenční služba** aktivity.</span><span class="sxs-lookup"><span data-stu-id="481d6-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>

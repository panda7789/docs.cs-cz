---
title: 'Postupy: Vytvoření služby pracovních postupů, která volá jinou službu pracovních postupů'
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: 1b30da34f7c85cccd98b18cd32b81c83630989b2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216129"
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a><span data-ttu-id="fe8f5-102">Postupy: Vytvoření služby pracovních postupů, která volá jinou službu pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="fe8f5-102">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>

<span data-ttu-id="fe8f5-103">Někdy je nezbytné služby pracovního postupu k získání informací z jiné služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-103">It is sometimes necessary for a workflow service to obtain information from another workflow service.</span></span> <span data-ttu-id="fe8f5-104">Toto téma ukazuje, jak z jiného volání jedné služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-104">This topic demonstrates how to call one workflow service from another.</span></span> <span data-ttu-id="fe8f5-105">V tomto tématu vytvoříme dvě služby pracovního postupu; jeden, který obsahuje metodu, která obrací vstupního řetězce a druhý, který převede vstupní řetězec na velká písmena po vrácení řetězec, který používá službu první.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-105">In this topic, we’ll create two workflow services; one that has a method that reverses the input string, and another that converts the input string to uppercase after reversing the string that uses the first service.</span></span>

### <a name="to-create-the-reverser-workflow-service"></a><span data-ttu-id="fe8f5-106">Vytvoření služby pracovního postupu Reverser</span><span class="sxs-lookup"><span data-stu-id="fe8f5-106">To create the Reverser workflow service</span></span>

1.  <span data-ttu-id="fe8f5-107">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-107">Open Visual Studio.</span></span>

2.  <span data-ttu-id="fe8f5-108">Vyberte **souboru** > **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-108">Select **File** > **New Project**.</span></span> <span data-ttu-id="fe8f5-109">V části **pracovního postupu** uzlu **nainstalované šablony** vyberte **aplikace služeb pracovního postupu WCF**.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-109">Under the **Workflow** node in the **Installed Templates** pane, select **WCF Workflow Service Application**.</span></span> <span data-ttu-id="fe8f5-110">Pojmenujte řešení `NestedServices` a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-110">Name the solution `NestedServices` and then click **OK**.</span></span>

3.  <span data-ttu-id="fe8f5-111">V části **servery**, ujistěte se, že **použití místní webový Server IIS** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-111">Under **Servers**, make sure that **Use Local IIS Web Server** is selected.</span></span> <span data-ttu-id="fe8f5-112">Klikněte na tlačítko **vytvořit virtuální adresář**.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-112">Click **Create Virtual Directory**.</span></span> <span data-ttu-id="fe8f5-113">Klikněte na tlačítko **OK** v dialogové okno oznamující, že byl úspěšně vytvořen virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-113">Click **OK** in the dialog box stating that the virtual directory was successfully created.</span></span>

4.  <span data-ttu-id="fe8f5-114">V Průzkumníku řešení, přejmenujte Service1.xamlx k `StringReverserService.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-114">In Solution Explorer, rename Service1.xamlx to `StringReverserService.xamlx`.</span></span>

5.  <span data-ttu-id="fe8f5-115">Na **vlastnosti projektu** stránky pro nový projekt, klikněte na tlačítko **webové** kartu. Nastavte **spustit akci** k **konkrétní stránka**a vyberte StringReverserService.xamlx jako stránky a spustit.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-115">On the **Project Properties** page for the new project, click the **Web** tab. Set the **Start Action** to **Specific Page**, and select StringReverserService.xamlx as the page to start.</span></span>

6.  <span data-ttu-id="fe8f5-116">V Návrháři otevřete StringReverserService.xamlx a odstranit existující `ReceiveRequest` a `SendReply` aktivit a pak přetáhněte `ReceiveAndSendReply` aktivity do existující sekvenční aktivity.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-116">Open StringReverserService.xamlx in the designer and delete the existing `ReceiveRequest` and `SendReply` activities, and then drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>

    1.  <span data-ttu-id="fe8f5-117">Nastavte **OperationName** k ReverseString.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-117">Set the **OperationName** to ReverseString.</span></span>

    2.  <span data-ttu-id="fe8f5-118">Nastavte **ServiceContractName** k IReverseString.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-118">Set the **ServiceContractName** to IReverseString.</span></span>

    3.  <span data-ttu-id="fe8f5-119">Vyberte **CanCreateInstance** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-119">Select the **CanCreateInstance** check box.</span></span>

7.  <span data-ttu-id="fe8f5-120">Vyberte **SequentialService** aktivitu a pak klikněte na tlačítko **proměnné** karta v dolní části návrháře.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-120">Select the **SequentialService** activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="fe8f5-121">Vytvořte dvě nové proměnné s názvem StringToReverse a ReversedStringToReturn typu String.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-121">Create two new variables named StringToReverse and ReversedStringToReturn of type String.</span></span>

8.  <span data-ttu-id="fe8f5-122">Klikněte na tlačítko **definovat** odkaz v **Receive** aktivity.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-122">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="fe8f5-123">Klikněte na tlačítko **parametry**a vytvořit parametr s názvem InputString typu řetězec, který se přiřadí StringToReverse.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-123">Click the  **Parameters**, and create a parameter named InputString of type String that assigns to StringToReverse.</span></span>

9. <span data-ttu-id="fe8f5-124">Klikněte na tlačítko **definovat** propojit **SendReplyToReceive** aktivity.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-124">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="fe8f5-125">Klikněte na tlačítko **parametry**a vytvořit parametr s názvem ReversedString typu String, přiřazená ReversedStringToReturn.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-125">Click the **Parameters**, and create a parameter named ReversedString of type String, assigned to ReversedStringToReturn.</span></span>

10. <span data-ttu-id="fe8f5-126">Implementovat logiku pro službu, vytvořte novou třídu v projektu volá StringLibrary.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-126">To implement the logic for the service, create a new class in the project called StringLibrary.</span></span>  <span data-ttu-id="fe8f5-127">Nahraďte definici třídy následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-127">Replace the class definition with the following code.</span></span>

    ```
    public class StringLibrary
        {
            public static String ReverseString(string StringToReverse)
            {
                char[] charArray = StringToReverse.ToCharArray();
                Array.Reverse(charArray);
                return new String(charArray);
            }
        }
    ```

11. <span data-ttu-id="fe8f5-128">Chcete-li volat metodu ReverseString na vstupu, přetáhněte **InvokeMethod** aktivitu z panelu nástrojů do prostoru mezi **Receive** a **odeslání odpovědi SendReply** aktivity.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-128">To call the ReverseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="fe8f5-129">Nastavte vlastnosti aktivity následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fe8f5-129">Set the properties of the activity as follows:</span></span>

    1.  <span data-ttu-id="fe8f5-130">**MethodName**: ReverseString</span><span class="sxs-lookup"><span data-stu-id="fe8f5-130">**MethodName**: ReverseString</span></span>

    2.  <span data-ttu-id="fe8f5-131">**Výsledek**: ReversedStringToReturn</span><span class="sxs-lookup"><span data-stu-id="fe8f5-131">**Result**: ReversedStringToReturn</span></span>

    3.  <span data-ttu-id="fe8f5-132">**Parametry**: vytvoří nový parametr s **směr** nástroje v aplikaci, **typ** řetězce a **hodnota** z StringToReverse.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-132">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToReverse.</span></span>

    4.  <span data-ttu-id="fe8f5-133">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="fe8f5-133">**TargetType**: NestedServices.StringLibrary</span></span>

12. <span data-ttu-id="fe8f5-134">Pokud chcete službu otestujte stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-134">Test the service by pressing F5.</span></span> <span data-ttu-id="fe8f5-135">Testovací klient WCF, který se zobrazí klikněte dvakrát na metodu ReverseString().</span><span class="sxs-lookup"><span data-stu-id="fe8f5-135">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="fe8f5-136">V podokně požadavku zadejte `Sample` pro hodnoty parametru InputString.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-136">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="fe8f5-137">Klikněte na tlačítko **vyvolat**.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-137">Click **Invoke**.</span></span> <span data-ttu-id="fe8f5-138">Služba by měla vrátit "elpmaS".</span><span class="sxs-lookup"><span data-stu-id="fe8f5-138">The service should return "elpmaS".</span></span>

### <a name="to-create-the-uppercaser-workflow-service"></a><span data-ttu-id="fe8f5-139">Vytvoření služby pracovního postupu UpperCaser</span><span class="sxs-lookup"><span data-stu-id="fe8f5-139">To create the UpperCaser workflow service</span></span>

1.  <span data-ttu-id="fe8f5-140">Klikněte pravým tlačítkem na projekt NestedServices a vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-140">Right-click the NestedServices project and select **Add** > **New Item**.</span></span> <span data-ttu-id="fe8f5-141">V **pracovního postupu** uzlu, vyberte **služby pracovního postupu WCF**a pojmenujte novou službu `UpperCaserService`.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-141">In the **Workflow** node, select **WCF Workflow Service**, and name the new service `UpperCaserService`.</span></span> <span data-ttu-id="fe8f5-142">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-142">Click **Add**.</span></span> <span data-ttu-id="fe8f5-143">To byste přidat nový pracovní postup služby zvané UpperCaserService.xamlx do projektu.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-143">This should add a new workflow service called UpperCaserService.xamlx to the project.</span></span>

2.  <span data-ttu-id="fe8f5-144">V Návrháři otevřete UpperCaserService.xamlx a odstranit existující **ReceiveRequest** a `SendReply` aktivity a přetáhněte `ReceiveAndSendReply` aktivity do existující sekvenční aktivity.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-144">Open UpperCaserService.xamlx in the designer and delete the existing **ReceiveRequest** and `SendReply` activities, and drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>

    1.  <span data-ttu-id="fe8f5-145">Nastavte **OperationName** k UpperCaseString.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-145">Set the **OperationName** to UpperCaseString.</span></span>

    2.  <span data-ttu-id="fe8f5-146">Nastavte **ServiceContractName** k IUpperCaseString.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-146">Set the **ServiceContractName** to IUpperCaseString.</span></span>

    3.  <span data-ttu-id="fe8f5-147">Vyberte **CanCreateInstance** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-147">Select the **CanCreateInstance** check box.</span></span>

3.  <span data-ttu-id="fe8f5-148">Vybrat aktivitu SequentialService a potom klikněte na tlačítko **proměnné** karta v dolní části návrháře.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-148">Select the SequentialService activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="fe8f5-149">Vytvořte tři nové proměnné s názvem StringToUpper StringToReverse a StringToReturn typu String.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-149">Create three new variables named StringToUpper, StringToReverse, and StringToReturn of type String.</span></span>

4.  <span data-ttu-id="fe8f5-150">Klikněte na tlačítko **definovat** odkaz v **Receive** aktivity.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-150">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="fe8f5-151">Klikněte na tlačítko **parametry**a vytvořit parametr s názvem InputString typu řetězec, který se přiřadí StringToUpper.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-151">Click the **Parameters**, and create a parameter named InputString of type String that assigns to StringToUpper.</span></span>

5.  <span data-ttu-id="fe8f5-152">Klikněte na tlačítko **definovat** propojit **SendReplyToReceive** aktivity.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-152">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="fe8f5-153">Klikněte na tlačítko **parametry**a vytvořit parametr s názvem ModifiedString typu String, přiřazená StringToReturn.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-153">Click the **Parameters**, and create a parameter named ModifiedString of type String, assigned to StringToReturn.</span></span>

6.  <span data-ttu-id="fe8f5-154">Pokud chcete implementovat logiku pro služby, vytvoření nové metody ve třídě StringLibrary pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-154">To implement the logic for the service, create a new method in the StringLibrary class using the following code.</span></span>

    ```
    public static String UpperCaseString(string StringToUpperCase)
    {
         return StringToUpperCase.ToUpper();

    }
    ```

7.  <span data-ttu-id="fe8f5-155">Chcete-li volat metodu UpperCaseString na vstupu, přetáhněte **InvokeMethod** aktivitu z panelu nástrojů do prostoru mezi **Receive** a **odeslání odpovědi SendReply** aktivity.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-155">To call the UpperCaseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="fe8f5-156">Nastavte vlastnosti aktivity následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fe8f5-156">Set the properties of the activity as follows:</span></span>

    1.  <span data-ttu-id="fe8f5-157">**MethodName**: UpperCaseString</span><span class="sxs-lookup"><span data-stu-id="fe8f5-157">**MethodName**: UpperCaseString</span></span>

    2.  <span data-ttu-id="fe8f5-158">**Výsledek**: StringToReverse</span><span class="sxs-lookup"><span data-stu-id="fe8f5-158">**Result**: StringToReverse</span></span>

    3.  <span data-ttu-id="fe8f5-159">**Parametry**: vytvoří nový parametr s **směr** nástroje v aplikaci, **typ** řetězce a **hodnota** z StringToUpper.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-159">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToUpper.</span></span>

    4.  <span data-ttu-id="fe8f5-160">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="fe8f5-160">**TargetType**: NestedServices.StringLibrary</span></span>

8.  <span data-ttu-id="fe8f5-161">Nyní zavoláme vám první služby na upravený řetězec.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-161">We’ll now call the first service on the modified string.</span></span> <span data-ttu-id="fe8f5-162">Klikněte pravým tlačítkem na projekt a vyberte **přidat** > **odkaz na službu**.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-162">Right-click the project and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="fe8f5-163">Přidání odkazu na službu na službu na http://localhost/NestedServices/StringReverserService.xamlx a sestavte projekt a vytvořit vlastní aktivitu pro přístup k webové službě první.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-163">Add a service reference to the service at http://localhost/NestedServices/StringReverserService.xamlx and build the project to create a custom activity to access the first Web service.</span></span>

9. <span data-ttu-id="fe8f5-164">Přetáhněte instance novou aktivitu do pracovního postupu, mezi **InvokeMethod** aktivity a **SendReplyToReceive** aktivity.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-164">Drag an instance of the new activity onto the workflow, between the **InvokeMethod** activity and the **SendReplyToReceive** activities.</span></span> <span data-ttu-id="fe8f5-165">Přiřaďte proměnné StringToReverse vlastnost InputString nová aktivita a proměnné StringToReturn StringToReturn vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-165">Assign the variable StringToReverse to the InputString property of the new activity, and the variable StringToReturn to the StringToReturn property.</span></span>

10. <span data-ttu-id="fe8f5-166">Otevřete stránku vlastností pro projekt NestedServices a změnit **konkrétní stránka** v **webové** kartu UpperCaserService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-166">Open the Properties page for the NestedServices project, and change the **Specific Page** in the **Web** tab to UpperCaserService.xamlx.</span></span>

11. <span data-ttu-id="fe8f5-167">Pokud chcete službu otestujte stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-167">Test the service by pressing F5.</span></span> <span data-ttu-id="fe8f5-168">Testovací klient WCF, který se zobrazí klikněte dvakrát na metodu ReverseString().</span><span class="sxs-lookup"><span data-stu-id="fe8f5-168">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="fe8f5-169">V podokně požadavku zadejte `Sample` pro hodnoty parametru InputString.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-169">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="fe8f5-170">Klikněte na tlačítko **vyvolat**.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-170">Click **Invoke**.</span></span> <span data-ttu-id="fe8f5-171">Služba by měla vrátit "ELPMAS".</span><span class="sxs-lookup"><span data-stu-id="fe8f5-171">The service should return "ELPMAS".</span></span>

### <a name="to-create-a-client-to-call-the-services"></a><span data-ttu-id="fe8f5-172">K vytvoření klienta k volání služeb</span><span class="sxs-lookup"><span data-stu-id="fe8f5-172">To create a client to call the services</span></span>

1.  <span data-ttu-id="fe8f5-173">Přidáte nový projekt konzolové aplikace volá klienta do řešení.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-173">Add a new Console application project called Client to the solution.</span></span>

2.  <span data-ttu-id="fe8f5-174">Klikněte pravým tlačítkem na klientský projekt a vyberte **přidat** > **odkaz na službu**.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-174">Right-click the Client project and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="fe8f5-175">V okně, které se zobrazí, klikněte na tlačítko **Discover**.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-175">In the window that appears, click **Discover**.</span></span> <span data-ttu-id="fe8f5-176">Vyberte StringReverserService.xamlx a zadejte ReverseService jako obor názvů.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-176">Select StringReverserService.xamlx, and enter ReverseService as the namespace.</span></span>  <span data-ttu-id="fe8f5-177">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-177">Click **OK**.</span></span>

3.  <span data-ttu-id="fe8f5-178">Metoda Main v souboru Program.cs nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="fe8f5-178">Replace the Main method in Program.cs with the following code.</span></span>

    ```
    static void Main(string[] args)
    {
        Console.Write("Input string to process:");
        String input = Console.ReadLine();
        var service = new ReverseService.ReverseStringClient();
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));
        Console.ReadKey();
    }
    ```
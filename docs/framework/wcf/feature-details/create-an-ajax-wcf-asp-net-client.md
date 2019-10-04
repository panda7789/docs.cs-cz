---
title: Vytvoření služby WCF s povoleným AJAX a klienta ASP.NET v aplikaci Visual Studio
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: a6d6e87de6200a5cb9bba566d595066673cdf9cf
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834779"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="0c55e-102">Postupy: Vytvoření služby WCF, ve které je povolený AJAX, a klienta ASP.NET přistupujícího k ní</span><span class="sxs-lookup"><span data-stu-id="0c55e-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="0c55e-103">V tomto tématu se dozvíte, jak pomocí sady Visual Studio vytvořit službu WCF (Windows Communication Foundation s podporou AJAX) a klienta ASP.NET, který přistupuje ke službě.</span><span class="sxs-lookup"><span data-stu-id="0c55e-103">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="0c55e-104">Vytvoření webové aplikace v ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0c55e-104">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="0c55e-105">Otevřete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0c55e-105">Open Visual Studio.</span></span>

1. <span data-ttu-id="0c55e-106">V nabídce **soubor** vyberte **Nový** **projekt**  > .</span><span class="sxs-lookup"><span data-stu-id="0c55e-106">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="0c55e-107">V dialogovém okně **Nový projekt** rozbalte položku **nainstalovaná** > **Webová** kategorie**C#Visual** >  a pak vyberte **ASP.NET webová aplikace (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="0c55e-107">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="0c55e-108">Pojmenujte projekt **SandwichServices** a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="0c55e-108">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="0c55e-109">V dialogovém okně **Nová webová aplikace ASP.NET** vyberte **prázdné** a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="0c55e-109">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![Dialog webové aplikace v ASP.NET v aplikaci Visual Studio](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="0c55e-111">Přidat webový formulář</span><span class="sxs-lookup"><span data-stu-id="0c55e-111">Add a web form</span></span>

1. <span data-ttu-id="0c55e-112">V **Průzkumník řešení** klikněte pravým tlačítkem na projekt SandwichServices a vyberte **přidat** **novou položku** > .</span><span class="sxs-lookup"><span data-stu-id="0c55e-112">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="0c55e-113">V dialogovém okně **Přidat novou položku** rozbalte položku **nainstalovaná** > **Webová** kategorie**C#Visual** >  a pak vyberte šablonu **webového formuláře** .</span><span class="sxs-lookup"><span data-stu-id="0c55e-113">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="0c55e-114">Přijměte výchozí název (**WebForm1**) a pak vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="0c55e-114">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="0c55e-115">*WebForm1. aspx* se otevře v zobrazení **zdroje** .</span><span class="sxs-lookup"><span data-stu-id="0c55e-115">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="0c55e-116">Do značek **> @no__t 1Body** přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="0c55e-116">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="0c55e-117">Vytvoření služby WCF s povoleným AJAX</span><span class="sxs-lookup"><span data-stu-id="0c55e-117">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="0c55e-118">V **Průzkumník řešení** klikněte pravým tlačítkem na projekt SandwichServices a vyberte **přidat** **novou položku** > .</span><span class="sxs-lookup"><span data-stu-id="0c55e-118">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="0c55e-119">V dialogovém okně **Přidat novou položku** rozbalte položku **nainstalovaná** > **Webová** kategorie**Visual C#**  >  a vyberte šablonu **Služba WCF (s podporou jazyka AJAX)** .</span><span class="sxs-lookup"><span data-stu-id="0c55e-119">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Šablona položky služby WCF (s podporou jazyka AJAX) v aplikaci Visual Studio](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="0c55e-121">Pojmenujte službu **CostService** a pak vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="0c55e-121">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="0c55e-122">*CostService.svc.cs* se otevře v editoru.</span><span class="sxs-lookup"><span data-stu-id="0c55e-122">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="0c55e-123">Implementujte operaci ve službě.</span><span class="sxs-lookup"><span data-stu-id="0c55e-123">Implement the operation in the service.</span></span> <span data-ttu-id="0c55e-124">Přidejte následující metodu do třídy CostService, která vypočítá náklady na množství sandwichovych hodnot:</span><span class="sxs-lookup"><span data-stu-id="0c55e-124">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="0c55e-125">Konfigurace klienta pro přístup ke službě</span><span class="sxs-lookup"><span data-stu-id="0c55e-125">Configure the client to access the service</span></span>

1. <span data-ttu-id="0c55e-126">Otevřete soubor *WebForm1. aspx* a vyberte **návrhové** zobrazení.</span><span class="sxs-lookup"><span data-stu-id="0c55e-126">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="0c55e-127">V nabídce **zobrazení** vyberte položku **Sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="0c55e-127">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="0c55e-128">Rozbalte uzel **rozšíření AJAX** a přetáhněte objekt **ScriptManager** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="0c55e-128">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="0c55e-129">Zpět v zobrazení **zdroje** přidejte následující kód mezi značkami **\<ScriptManager >** a určete cestu ke službě WCF:</span><span class="sxs-lookup"><span data-stu-id="0c55e-129">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. <span data-ttu-id="0c55e-130">Přidejte kód pro funkci JavaScriptu `Calculate()`.</span><span class="sxs-lookup"><span data-stu-id="0c55e-130">Add the code for the Javascript function `Calculate()`.</span></span> <span data-ttu-id="0c55e-131">Vložte následující kód do části **head** webového formuláře:</span><span class="sxs-lookup"><span data-stu-id="0c55e-131">Place the following code in the **head** section of the web form:</span></span>

    ```html
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
    ```

   <span data-ttu-id="0c55e-132">Tento kód volá metodu CostService pro výpočet ceny pro tři Sandwichovy a pak výsledek zobrazí v rozpětí s názvem **additionResult**.</span><span class="sxs-lookup"><span data-stu-id="0c55e-132">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="0c55e-133">Spustit program</span><span class="sxs-lookup"><span data-stu-id="0c55e-133">Run the program</span></span>

<span data-ttu-id="0c55e-134">Ujistěte se, že má *WebForm1. aspx* fokus a pak stiskněte tlačítko **Start** pro spuštění webového klienta.</span><span class="sxs-lookup"><span data-stu-id="0c55e-134">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="0c55e-135">Tlačítko má zelený trojúhelník a říká něco jako **IIS Express (Microsoft Edge)** .</span><span class="sxs-lookup"><span data-stu-id="0c55e-135">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="0c55e-136">Případně můžete stisknout klávesu <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0c55e-136">Or, you can press <kbd>F5</kbd>.</span></span> <span data-ttu-id="0c55e-137">Kliknutím na tlačítko **cena za 3 sandwichovys** vygenerujete očekávaný výstup "3,75".</span><span class="sxs-lookup"><span data-stu-id="0c55e-137">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example"></a><span data-ttu-id="0c55e-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c55e-138">Example</span></span>

<span data-ttu-id="0c55e-139">Následující je úplný kód v souboru *CostService.svc.cs* :</span><span class="sxs-lookup"><span data-stu-id="0c55e-139">The following is the full code in the *CostService.svc.cs* file:</span></span>

```csharp
using System.ServiceModel;
using System.ServiceModel.Activation;

namespace SandwichServices
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class CostService
    {
        [OperationContract]
        public double CostOfSandwiches(int quantity)
        {
            return 1.25 * quantity;
        }
    }
}
```

<span data-ttu-id="0c55e-140">Toto je úplný obsah stránky *WebForm1. aspx* :</span><span class="sxs-lookup"><span data-stu-id="0c55e-140">The following is the full contents of the *WebForm1.aspx* page:</span></span>

```aspx-csharp
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SandwichServices.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
</head>
<body>
    <form id="form1" runat="server">
        <div>
        </div>
        <asp:ScriptManager ID="ScriptManager1" runat="server">
            <Services>
                <asp:ServiceReference Path="~/CostService.svc" />
            </Services>
        </asp:ScriptManager>

        <input type="button" value="Price of 3 sandwiches" onclick="Calculate()" />
        <br />
        <span id="additionResult"></span>
    </form>
</body>
</html>
```

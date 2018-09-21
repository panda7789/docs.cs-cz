---
title: Vytvoření služby WCF s podporou jazyka AJAX a klienta ASP.NET v sadě Visual Studio
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 954ee0409f370c3fa28814a70d51334fd75f7b79
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46528837"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="6c60b-102">Postupy: Vytvoření služby WCF, ve které je povolený AJAX, a klienta ASP.NET přistupujícího k ní</span><span class="sxs-lookup"><span data-stu-id="6c60b-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="6c60b-103">Toto téma ukazuje, jak pomocí sady Visual Studio k vytvoření služby s povoleným AJAX Windows Communication Foundation (WCF) a klienta ASP.NET přistupujícího k ní.</span><span class="sxs-lookup"><span data-stu-id="6c60b-103">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="6c60b-104">Vytvoření webové aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c60b-104">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="6c60b-105">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6c60b-105">Open Visual Studio.</span></span>

1. <span data-ttu-id="6c60b-106">Z **souboru** nabídce vyberte možnost **nový** > **projektu**</span><span class="sxs-lookup"><span data-stu-id="6c60b-106">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="6c60b-107">V **nový projekt** dialogového okna, rozbalte **nainstalováno** > **Visual C#** > **webové** kategorie a pak Vyberte **webová aplikace ASP.NET (.NET Framework)**.</span><span class="sxs-lookup"><span data-stu-id="6c60b-107">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="6c60b-108">Pojmenujte projekt **SandwichServices** a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c60b-108">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="6c60b-109">V **nová webová aplikace ASP.NET** dialogového okna, vyberte **prázdný** a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c60b-109">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![Technologie ASP.NET webové aplikace typu dialogu v sadě Visual Studio](media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="6c60b-111">Přidejte webový formulář</span><span class="sxs-lookup"><span data-stu-id="6c60b-111">Add a web form</span></span>

1. <span data-ttu-id="6c60b-112">Klikněte pravým tlačítkem na projekt SandwichServices v **Průzkumníka řešení** a vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="6c60b-112">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="6c60b-113">V **přidat novou položku** dialogového okna, rozbalte **nainstalováno** > **Visual C#** > **webové** kategorie a pak Vyberte **webový formulář** šablony.</span><span class="sxs-lookup"><span data-stu-id="6c60b-113">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="6c60b-114">Přijměte výchozí název (**formulář WebForm1**) a pak vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="6c60b-114">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="6c60b-115">*WebForm1.aspx* se otevře v **zdroj** zobrazení.</span><span class="sxs-lookup"><span data-stu-id="6c60b-115">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="6c60b-116">Přidejte následující kód uvnitř  **\<text >** značky:</span><span class="sxs-lookup"><span data-stu-id="6c60b-116">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="6c60b-117">Vytvoření služby WCF s podporou jazyka AJAX</span><span class="sxs-lookup"><span data-stu-id="6c60b-117">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="6c60b-118">Klikněte pravým tlačítkem na projekt SandwichServices v **Průzkumníka řešení** a vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="6c60b-118">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="6c60b-119">V **přidat novou položku** dialogového okna, rozbalte **nainstalováno** > **Visual C#** > **webové** kategorie a pak Vyberte **služby WCF (podporou jazyka AJAX)** šablony.</span><span class="sxs-lookup"><span data-stu-id="6c60b-119">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Šablona služby WCF (podporou jazyka AJAX) položku v sadě Visual Studio](media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="6c60b-121">Pojmenujte službu **CostService** a pak vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="6c60b-121">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="6c60b-122">*CostService.svc.cs* otevře v editoru.</span><span class="sxs-lookup"><span data-stu-id="6c60b-122">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="6c60b-123">Implementace operace ve službě.</span><span class="sxs-lookup"><span data-stu-id="6c60b-123">Implement the operation in the service.</span></span> <span data-ttu-id="6c60b-124">Přidejte následující metodu do třídy CostService vypočítat náklady na množství sendviče:</span><span class="sxs-lookup"><span data-stu-id="6c60b-124">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="6c60b-125">Konfigurace klienta pro přístup ke službě</span><span class="sxs-lookup"><span data-stu-id="6c60b-125">Configure the client to access the service</span></span>

1. <span data-ttu-id="6c60b-126">Otevřít *WebForm1.aspx* a vyberte možnost **návrhu** zobrazení.</span><span class="sxs-lookup"><span data-stu-id="6c60b-126">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="6c60b-127">Z **zobrazení** nabídce vyberte možnost **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="6c60b-127">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="6c60b-128">Rozbalte **rozšíření AJAX** uzlu a přetáhněte **ScriptManager** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="6c60b-128">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="6c60b-129">Zpátky **zdroj** zobrazení, přidejte následující kód mezi  **\<ovládacímu prvku ScriptManager >** značky a zadejte cestu ke službě WCF:</span><span class="sxs-lookup"><span data-stu-id="6c60b-129">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```html
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

1. <span data-ttu-id="6c60b-130">Přidejte kód pro funkce jazyka Javascript `Calculate()`.</span><span class="sxs-lookup"><span data-stu-id="6c60b-130">Add the code for the Javascript function `Calculate()`.</span></span> <span data-ttu-id="6c60b-131">Umístěte následující kód **head** části webové formuláře:</span><span class="sxs-lookup"><span data-stu-id="6c60b-131">Place the following code in the **head** section of the web form:</span></span>

    ```javascript
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

   <span data-ttu-id="6c60b-132">Tento kód volá metodu CostService k výpočtu ceny pro tři sendviče a potom zobrazí výsledky v rozpětí volá **additionResult**.</span><span class="sxs-lookup"><span data-stu-id="6c60b-132">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="6c60b-133">Spuštění programu</span><span class="sxs-lookup"><span data-stu-id="6c60b-133">Run the program</span></span>

<span data-ttu-id="6c60b-134">Ujistěte se, že *WebForm1.aspx* má právě fokus a potom stiskněte klávesu **Start** tlačítko Spustit webový klient.</span><span class="sxs-lookup"><span data-stu-id="6c60b-134">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="6c60b-135">Tlačítko se zeleným trojúhelníkem a řekne něco jako **služby IIS Express (Microsoft Edge)**.</span><span class="sxs-lookup"><span data-stu-id="6c60b-135">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="6c60b-136">Nebo můžete stisknout **F5**.</span><span class="sxs-lookup"><span data-stu-id="6c60b-136">Or, you can press **F5**.</span></span> <span data-ttu-id="6c60b-137">Klikněte na tlačítko **cena 3 sendviče** pro vygenerování očekávaný výstup "3,75".</span><span class="sxs-lookup"><span data-stu-id="6c60b-137">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example-code"></a><span data-ttu-id="6c60b-138">Příklad kódu</span><span class="sxs-lookup"><span data-stu-id="6c60b-138">Example code</span></span>

<span data-ttu-id="6c60b-139">Tady je celý kód v *CostService.svc.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="6c60b-139">Following is the full code in the *CostService.svc.cs* file :</span></span>

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

<span data-ttu-id="6c60b-140">Následuje úplný obsah *WebForm1.aspx* stránky:</span><span class="sxs-lookup"><span data-stu-id="6c60b-140">Following is the full contents of the *WebForm1.aspx* page:</span></span>

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

---
title: Vytvoření služby WCF s podporou jazyka AJAX a klienta ASP.NET v sadě Visual Studio
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 954ee0409f370c3fa28814a70d51334fd75f7b79
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678279"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>Postupy: Vytvoření služby WCF, ve které je povolený AJAX, a klienta ASP.NET přistupujícího k ní

Toto téma ukazuje, jak pomocí sady Visual Studio k vytvoření služby s povoleným AJAX Windows Communication Foundation (WCF) a klienta ASP.NET přistupujícího k ní.

## <a name="create-an-aspnet-web-app"></a>Vytvoření webové aplikace ASP.NET

1. Otevřít Visual Studio.

1. Z **souboru** nabídce vyberte možnost **nový** > **projektu**

1. V **nový projekt** dialogového okna, rozbalte **nainstalováno** > **Visual C#** > **webové** kategorie a pak Vyberte **webová aplikace ASP.NET (.NET Framework)**.

1. Pojmenujte projekt **SandwichServices** a klikněte na tlačítko **OK**.

1. V **nová webová aplikace ASP.NET** dialogového okna, vyberte **prázdný** a pak vyberte **OK**.

   ![Technologie ASP.NET webové aplikace typu dialogu v sadě Visual Studio](media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a>Přidejte webový formulář

1. Klikněte pravým tlačítkem na projekt SandwichServices v **Průzkumníka řešení** a vyberte **přidat** > **nová položka**.

1. V **přidat novou položku** dialogového okna, rozbalte **nainstalováno** > **Visual C#** > **webové** kategorie a pak Vyberte **webový formulář** šablony.

1. Přijměte výchozí název (**formulář WebForm1**) a pak vyberte **přidat**.

   *WebForm1.aspx* se otevře v **zdroj** zobrazení.

1. Přidejte následující kód uvnitř  **\<text >** značky:

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a>Vytvoření služby WCF s podporou jazyka AJAX

1. Klikněte pravým tlačítkem na projekt SandwichServices v **Průzkumníka řešení** a vyberte **přidat** > **nová položka**.

1. V **přidat novou položku** dialogového okna, rozbalte **nainstalováno** > **Visual C#** > **webové** kategorie a pak Vyberte **služby WCF (podporou jazyka AJAX)** šablony.

   ![Šablona služby WCF (podporou jazyka AJAX) položku v sadě Visual Studio](media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. Pojmenujte službu **CostService** a pak vyberte **přidat**.

   *CostService.svc.cs* otevře v editoru.

1. Implementace operace ve službě. Přidejte následující metodu do třídy CostService vypočítat náklady na množství sendviče:

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a>Konfigurace klienta pro přístup ke službě

1. Otevřít *WebForm1.aspx* a vyberte možnost **návrhu** zobrazení.

2. Z **zobrazení** nabídce vyberte možnost **nástrojů**.

3. Rozbalte **rozšíření AJAX** uzlu a přetáhněte **ScriptManager** do formuláře.

4. Zpátky **zdroj** zobrazení, přidejte následující kód mezi  **\<ovládacímu prvku ScriptManager >** značky a zadejte cestu ke službě WCF:

    ```html
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

1. Přidejte kód pro funkce jazyka Javascript `Calculate()`. Umístěte následující kód **head** části webové formuláře:

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

   Tento kód volá metodu CostService k výpočtu ceny pro tři sendviče a potom zobrazí výsledky v rozpětí volá **additionResult**.

## <a name="run-the-program"></a>Spuštění programu

Ujistěte se, že *WebForm1.aspx* má právě fokus a potom stiskněte klávesu **Start** tlačítko Spustit webový klient. Tlačítko se zeleným trojúhelníkem a řekne něco jako **služby IIS Express (Microsoft Edge)**. Nebo můžete stisknout **F5**. Klikněte na tlačítko **cena 3 sendviče** pro vygenerování očekávaný výstup "3,75".

## <a name="example-code"></a>Příklad kódu

Tady je celý kód v *CostService.svc.cs* souboru:

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

Následuje úplný obsah *WebForm1.aspx* stránky:

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

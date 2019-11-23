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
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>Postupy: Vytvoření služby WCF, ve které je povolený AJAX, a klienta ASP.NET přistupujícího k ní

V tomto tématu se dozvíte, jak pomocí sady Visual Studio vytvořit službu WCF (Windows Communication Foundation s podporou AJAX) a klienta ASP.NET, který přistupuje ke službě.

## <a name="create-an-aspnet-web-app"></a>Vytvoření webové aplikace v ASP.NET

1. Otevřít Visual Studio.

1. V nabídce **soubor** vyberte **Nový** > **projekt** .

1. V dialogovém okně **Nový projekt** rozbalte položku **nainstalovaná** > **Visual C#**  > **Webová** kategorie a pak vyberte **ASP.NET webová aplikace (.NET Framework)** .

1. Pojmenujte projekt **SandwichServices** a klikněte na **OK**.

1. V dialogovém okně **Nová webová aplikace ASP.NET** vyberte **prázdné** a pak vyberte **OK**.

   ![Dialog webové aplikace v ASP.NET v aplikaci Visual Studio](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a>Přidat webový formulář

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt SandwichServices a vyberte **Přidat** > **Nová položka**.

1. V dialogovém okně **Přidat novou položku** rozbalte položku **nainstalovaná** > **Visual C#**  > **webové** kategorie a pak vyberte šablonu **webového formuláře** .

1. Přijměte výchozí název (**WebForm1**) a pak vyberte **Přidat**.

   *WebForm1. aspx* se otevře v zobrazení **zdroje** .

1. Do **\<těla >** značky přidejte následující kód:

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a>Vytvoření služby WCF s povoleným AJAX

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt SandwichServices a vyberte **Přidat** > **Nová položka**.

1. V dialogovém okně **Přidat novou položku** rozbalte položku **nainstalovaná** > **Visual C#**  > **Web** a potom vyberte šablonu **služby WCF (s podporou jazyka AJAX)** .

   ![Šablona položky služby WCF (s podporou jazyka AJAX) v aplikaci Visual Studio](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. Pojmenujte službu **CostService** a pak vyberte **Přidat**.

   *CostService.svc.cs* se otevře v editoru.

1. Implementujte operaci ve službě. Přidejte následující metodu do třídy CostService, která vypočítá náklady na množství sandwichovych hodnot:

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a>Konfigurace klienta pro přístup ke službě

1. Otevřete soubor *WebForm1. aspx* a vyberte **návrhové** zobrazení.

2. V nabídce **zobrazení** vyberte položku **Sada nástrojů**.

3. Rozbalte uzel **rozšíření AJAX** a přetáhněte objekt **ScriptManager** do formuláře.

4. Zpět v zobrazení **zdroje** přidejte následující kód mezi **\<značky > ScriptManager** k určení cesty ke službě WCF:

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. Přidejte kód pro funkci JavaScriptu `Calculate()`. Vložte následující kód do části **head** webového formuláře:

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

   Tento kód volá metodu CostService pro výpočet ceny pro tři Sandwichovy a pak výsledek zobrazí v rozpětí s názvem **additionResult**.

## <a name="run-the-program"></a>Spuštění programu

Ujistěte se, že má *WebForm1. aspx* fokus a pak stiskněte tlačítko **Start** pro spuštění webového klienta. Tlačítko má zelený trojúhelník a říká něco jako **IIS Express (Microsoft Edge)** . Případně můžete stisknout klávesu <kbd>F5</kbd>. Kliknutím na tlačítko **cena za 3 sandwichovys** vygenerujete očekávaný výstup "3,75".

## <a name="example"></a>Příklad

Následující je úplný kód v souboru *CostService.svc.cs* :

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

Toto je úplný obsah stránky *WebForm1. aspx* :

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

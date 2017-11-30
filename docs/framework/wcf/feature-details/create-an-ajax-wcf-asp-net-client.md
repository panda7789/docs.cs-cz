---
title: "Postupy: Vytvoření služby WCF, ve které je povolený AJAX, a klienta ASP.NET přistupujícího k ní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a45a186b0d281976f3d6ad554d75742ba0f1cd50
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>Postupy: Vytvoření služby WCF, ve které je povolený AJAX, a klienta ASP.NET přistupujícího k ní
Toto téma ukazuje, jak vytvořit, podporou AJAXU pomocí sady Visual Studio 2008 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby a klienta ASP.NET přistupujícího k ní. Kód pro službu a klienta jsou uvedeny v části Příklad po kroky pro jejich vytváření jsou popsány v části postupy.  
  
### <a name="to-create-the-aspnet-client-application"></a>Chcete-li vytvořit klienta aplikace ASP.NET  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Z **soubor** nabídce vyberte možnost **nový**, pak **projektu**, pak **webové**a potom vyberte **webovéaplikaceASP.NET**.  
  
3.  Název projektu `SandwichServices` a klikněte na tlačítko **OK**.  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a>Chcete-li vytvořit službu technologie WCF AJAX  
  
1.  Klikněte pravým tlačítkem myši `SandwichServices` projektu v **Průzkumníku řešení** a vyberte **přidat**, pak **nová položka**a potom **podporou AJAXU služby WCF** .  
  
2.  Název služby `CostService` v **název** pole a klikněte na tlačítko **přidat**.  
  
3.  Otevřete soubor CostService.svc.cs.  
  
4.  Zadejte `Namespace` pro <xref:System.ServiceModel.ServiceContractAttribute> jako `SandwichService`:  
  
    ```  
    namespace SandwichServices  
    {  
      [ServiceContract(Namespace = "SandwichServices")]  
      [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
       public class CostService  
       {  
         …  
       }  
     }  
    ```  
  
5.  Implementace operace ve službě. Přidat <xref:System.ServiceModel.OperationContractAttribute> všechny operace, které označuje, že jsou součástí smlouvy. Následující příklad implementuje metodu, která vrátí náklady na dané množství sendviče.  
  
    ```  
    public class CostService  
    {  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
    // Add more operations here and mark them with [OperationContract]  
    }  
    ```  
  
### <a name="to-configure-the-client-to-access-the-service"></a>Abyste mohli nakonfigurovat klienta k přístupu ke službě  
  
1.  Otevřete stránku Default.aspx a vyberte **návrhu** zobrazení.  
  
2.  Z **zobrazení** nabídce vyberte možnost **sada nástrojů**.  
  
3.  Rozbalte **rozšíření AJAX** uzlu a přetažení **ScriptManager** na stránce Default.aspx.  
  
4.  Klikněte pravým tlačítkem myši **ScriptManager** a vyberte **vlastnosti**.  
  
5.  Rozbalte **služby** kolekce v **vlastnosti** okno otevře **kolekce ServiceReference** okno.  
  
6.  Klikněte na tlačítko **přidat**, zadejte `CostService.svc` jako **cesta** odkazuje a klikněte na tlačítko **OK**.  
  
7.  Rozbalte **HTML** uzel v **sada nástrojů** a přetažení **vstup (tlačítko)** na stránce Default.aspx.  
  
8.  Klikněte pravým tlačítkem myši **tlačítko** a vyberte **vlastnosti**.  
  
9. Změna **hodnotu** do `Price for 3 Sandwiches`.  
  
10. Dvakrát klikněte **tlačítko** pro přístup kód jazyka JavaScript.  
  
11. Následující kód v JavaScriptu v rámci předávat <`script`> elementu.  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a>Přístup ke službě z klienta  
  
1.  Pomocí kombinace kláves Ctrl + F5 spusťte službu a webového klienta. Klikněte **ceny pro 3 Grilled sendviče** pro vygenerování očekávaný výstup "3,75".  
  
## <a name="example"></a>Příklad  
 Tento příklad obsahuje kód služby obsažené v souboru WCFService.svc.cs a kódem klientské obsažené v souboru Default.aspx.  
  
```  
//The service code contained in the CostService.svc.cs file.  
  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace SandwichServices  
{  
    [ServiceContract(Namespace="SandwichServices")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class CostService  
    {  
        // Add [WebGet] attribute to use HTTP GET  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
        // Add more operations here and mark them with [OperationContract]  
    }  
}  
//The code for hosting the service is contained in the CostService.svc file.  
  
<%@ ServiceHost Language="C#" Debug="true" Service="SandwichServices.CostService" CodeBehind="CostService.svc.cs" %>  
  
//The client code contained in the Default.aspx file.  
  
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="SandwichServices._Default" %>  
  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
  
<html >  
<head runat="server">  
    <title>Untitled Page</title>  
<script language="javascript" type="text/javascript">  
// <!CDATA[  
  
function Button1_onclick() {  
var service = new SandwichServices.CostService();  
service.CostOfSandwiches(3, onSuccess, null, null);  
}  
  
function onSuccess(result){  
alert(result);  
}  
  
// ]]>  
</script>  
</head>  
<body>  
    <form id="form1" runat="server">  
    <div>  
  
    </div>  
    <asp:ScriptManager ID="ScriptManager1" runat="server">  
        <services>  
            <asp:servicereference Path="CostService.svc" />  
        </services>  
    </asp:ScriptManager>  
    </form>  
    <p>  
        <input id="Button1" type="button" value="Price for 3 Sandwiches" onclick="return Button1_onclick()" /></p>  
</body>  
</html>  
```     

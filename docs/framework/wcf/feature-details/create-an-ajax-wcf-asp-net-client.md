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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aafa15129e4a131c5f50eb3296a87fc141e1bda6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="5d69e-102">Postupy: Vytvoření služby WCF, ve které je povolený AJAX, a klienta ASP.NET přistupujícího k ní</span><span class="sxs-lookup"><span data-stu-id="5d69e-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>
<span data-ttu-id="5d69e-103">Toto téma ukazuje, jak vytvořit, podporou AJAXU pomocí sady Visual Studio 2008 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby a klienta ASP.NET přistupujícího k ní.</span><span class="sxs-lookup"><span data-stu-id="5d69e-103">This topic shows how to use Visual Studio 2008 to create an AJAX-enabled [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and an ASP.NET client that accesses the service.</span></span> <span data-ttu-id="5d69e-104">Kód pro službu a klienta jsou uvedeny v části Příklad po kroky pro jejich vytváření jsou popsány v části postupy.</span><span class="sxs-lookup"><span data-stu-id="5d69e-104">The code for the service and for the client are provided in the Example section after the steps for creating them are described in the Procedures section.</span></span>  
  
### <a name="to-create-the-aspnet-client-application"></a><span data-ttu-id="5d69e-105">Chcete-li vytvořit klienta aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5d69e-105">To create the ASP.NET client application</span></span>  
  
1.  <span data-ttu-id="5d69e-106">Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5d69e-106">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="5d69e-107">Z **soubor** nabídce vyberte možnost **nový**, pak **projektu**, pak **webové**a potom vyberte **webovéaplikaceASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="5d69e-107">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Application**.</span></span>  
  
3.  <span data-ttu-id="5d69e-108">Název projektu `SandwichServices` a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="5d69e-108">Name the Project `SandwichServices` and click **OK**.</span></span>  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a><span data-ttu-id="5d69e-109">Chcete-li vytvořit službu technologie WCF AJAX</span><span class="sxs-lookup"><span data-stu-id="5d69e-109">To create the WCF AJAX-enabled service</span></span>  
  
1.  <span data-ttu-id="5d69e-110">Klikněte pravým tlačítkem myši `SandwichServices` projektu v **Průzkumníku řešení** a vyberte **přidat**, pak **nová položka**a potom **podporou AJAXU služby WCF** .</span><span class="sxs-lookup"><span data-stu-id="5d69e-110">Right-click the `SandwichServices` project in the **Solution Explorer** window and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>  
  
2.  <span data-ttu-id="5d69e-111">Název služby `CostService` v **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="5d69e-111">Name the service `CostService` in the **Name** box and click **Add**.</span></span>  
  
3.  <span data-ttu-id="5d69e-112">Otevřete soubor CostService.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="5d69e-112">Open the CostService.svc.cs file.</span></span>  
  
4.  <span data-ttu-id="5d69e-113">Zadejte `Namespace` pro <xref:System.ServiceModel.ServiceContractAttribute> jako `SandwichService`:</span><span class="sxs-lookup"><span data-stu-id="5d69e-113">Specify the `Namespace` for <xref:System.ServiceModel.ServiceContractAttribute> as `SandwichService`:</span></span>  
  
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
  
5.  <span data-ttu-id="5d69e-114">Implementace operace ve službě.</span><span class="sxs-lookup"><span data-stu-id="5d69e-114">Implement the operations in the service.</span></span> <span data-ttu-id="5d69e-115">Přidat <xref:System.ServiceModel.OperationContractAttribute> všechny operace, které označuje, že jsou součástí smlouvy.</span><span class="sxs-lookup"><span data-stu-id="5d69e-115">Add the <xref:System.ServiceModel.OperationContractAttribute> to each of the operations to indicate that they are part of the contract.</span></span> <span data-ttu-id="5d69e-116">Následující příklad implementuje metodu, která vrátí náklady na dané množství sendviče.</span><span class="sxs-lookup"><span data-stu-id="5d69e-116">The following example implements a method that returns the cost of a given quantity of sandwiches.</span></span>  
  
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
  
### <a name="to-configure-the-client-to-access-the-service"></a><span data-ttu-id="5d69e-117">Abyste mohli nakonfigurovat klienta k přístupu ke službě</span><span class="sxs-lookup"><span data-stu-id="5d69e-117">To configure the client to access the service</span></span>  
  
1.  <span data-ttu-id="5d69e-118">Otevřete stránku Default.aspx a vyberte **návrhu** zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5d69e-118">Open the Default.aspx page and select the **Design** view.</span></span>  
  
2.  <span data-ttu-id="5d69e-119">Z **zobrazení** nabídce vyberte možnost **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="5d69e-119">From the **View** menu, select **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="5d69e-120">Rozbalte **rozšíření AJAX** uzlu a přetažení **ScriptManager** na stránce Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="5d69e-120">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** on to the Default.aspx page.</span></span>  
  
4.  <span data-ttu-id="5d69e-121">Klikněte pravým tlačítkem myši **ScriptManager** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5d69e-121">Right-click the **ScriptManager** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="5d69e-122">Rozbalte **služby** kolekce v **vlastnosti** okno otevře **kolekce ServiceReference** okno.</span><span class="sxs-lookup"><span data-stu-id="5d69e-122">Expand the **Services** collection in the **Properties** window to open up the **ServiceReference Collection Editor** window.</span></span>  
  
6.  <span data-ttu-id="5d69e-123">Klikněte na tlačítko **přidat**, zadejte `CostService.svc` jako **cesta** odkazuje a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="5d69e-123">Click **Add**, specify `CostService.svc` as the **Path** referenced, and click **OK**.</span></span>  
  
7.  <span data-ttu-id="5d69e-124">Rozbalte **HTML** uzel v **sada nástrojů** a přetažení **vstup (tlačítko)** na stránce Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="5d69e-124">Expand the **HTML** node in the **Toolbox** and drag and drop an **Input (Button)** on to the Default.aspx page.</span></span>  
  
8.  <span data-ttu-id="5d69e-125">Klikněte pravým tlačítkem myši **tlačítko** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5d69e-125">Right-click the **Button** and select **Properties**.</span></span>  
  
9. <span data-ttu-id="5d69e-126">Změna **hodnotu** do `Price for 3 Sandwiches`.</span><span class="sxs-lookup"><span data-stu-id="5d69e-126">Change the **Value** field to `Price for 3 Sandwiches`.</span></span>  
  
10. <span data-ttu-id="5d69e-127">Dvakrát klikněte **tlačítko** pro přístup kód jazyka JavaScript.</span><span class="sxs-lookup"><span data-stu-id="5d69e-127">Double-click the **Button** to access the JavaScript code.</span></span>  
  
11. <span data-ttu-id="5d69e-128">Následující kód v JavaScriptu v rámci předávat <`script`> elementu.</span><span class="sxs-lookup"><span data-stu-id="5d69e-128">Pass in the following JavaScript code within the <`script`> element.</span></span>  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a><span data-ttu-id="5d69e-129">Přístup ke službě z klienta</span><span class="sxs-lookup"><span data-stu-id="5d69e-129">To access the service from the client</span></span>  
  
1.  <span data-ttu-id="5d69e-130">Pomocí kombinace kláves Ctrl + F5 spusťte službu a webového klienta.</span><span class="sxs-lookup"><span data-stu-id="5d69e-130">Use Ctrl +F5 to launch the service and the Web client.</span></span> <span data-ttu-id="5d69e-131">Klikněte **ceny pro 3 Grilled sendviče** pro vygenerování očekávaný výstup "3,75".</span><span class="sxs-lookup"><span data-stu-id="5d69e-131">Click the **Price for 3 Grilled Sandwiches** button to generate the expected output of "3.75".</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d69e-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d69e-132">Example</span></span>  
 <span data-ttu-id="5d69e-133">Tento příklad obsahuje kód služby obsažené v souboru WCFService.svc.cs a kódem klientské obsažené v souboru Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="5d69e-133">This example contains the service code contained in the WCFService.svc.cs file and the client code contained in the Default.aspx file.</span></span>  
  
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

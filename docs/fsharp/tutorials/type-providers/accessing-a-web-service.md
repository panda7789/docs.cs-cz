---
title: "Návod - přístup k webové službě s použitím zprostředkovatelů typů (F #)"
description: "Naučte se používat pro přístup k službě WSDL webové služby popis Language (WSDL) typ zprostředkovatele, který je k dispozici v F # 3.0."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63374fa9-8fb8-43ac-bcb9-ef2290d9f851
ms.openlocfilehash: 06d955033d465cf58af05f483d21175f90d1777a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a><span data-ttu-id="986a0-104">Návod: Přístup k webové službě s použitím zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="986a0-104">Walkthrough: Accessing a Web Service by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="986a0-105">Tento průvodce byl vytvořen pro F # 3.0 a budou aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="986a0-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="986a0-106">V tématu [FSharp.Data](http://fsharp.github.io/FSharp.Data/) pro různé platformy, aktuální typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="986a0-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="986a0-107">Rozhraní API referenčních odkazů se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="986a0-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="986a0-108">Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="986a0-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="986a0-109">Tento návod ukazuje, jak použít typ poskytovatele služeb popis jazyka WSDL (Web), který je k dispozici v F # 3.0 pro přístup k službě WSDL.</span><span class="sxs-lookup"><span data-stu-id="986a0-109">This walkthrough shows you how to use the Web Services Description Language (WSDL) type provider that is available in F# 3.0 to access a WSDL service.</span></span> <span data-ttu-id="986a0-110">V dalších jazycích .NET generovat kód pro přístup k webové službě pomocí volání svcutil.exe nebo přidáním webový odkaz v například C# projektu získat chcete volat svcutil.exe pro vás Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="986a0-110">In other .NET languages, you generate the code to access the web service by calling svcutil.exe, or by adding a web reference in, for example, a C# project to get Visual Studio to call svcutil.exe for you.</span></span> <span data-ttu-id="986a0-111">V jazyce F # máte možnost navíc pomocí zprostředkovatele typu WSDL, takže co nejdříve můžete napsat kód, který vytváří wsdlservice – typ, typy jsou generovány a bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="986a0-111">In F#, you have the additional option of using the WSDL type provider, so as soon as you write the code that creates the WsdlService type, the types are generated and become available.</span></span> <span data-ttu-id="986a0-112">Tento proces závisí na službě, který je k dispozici při psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="986a0-112">This process relies on the service being available when you are writing the code.</span></span>

<span data-ttu-id="986a0-113">Tento návod ukazuje následující úlohy.</span><span class="sxs-lookup"><span data-stu-id="986a0-113">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="986a0-114">V tomto pořadí návod úspěšná, musíte provést je:</span><span class="sxs-lookup"><span data-stu-id="986a0-114">You must complete them in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="986a0-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="986a0-115">Creating the project</span></span>
<br />

- <span data-ttu-id="986a0-116">Konfigurace poskytovatele typu</span><span class="sxs-lookup"><span data-stu-id="986a0-116">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="986a0-117">Volání webové služby a zpracování výsledků</span><span class="sxs-lookup"><span data-stu-id="986a0-117">Calling the web service, and processing the results</span></span>
<br />


## <a name="creating-the-project"></a><span data-ttu-id="986a0-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="986a0-118">Creating the project</span></span>
<span data-ttu-id="986a0-119">V kroku vytvořte projekt a přidejte příslušné odkazy na pro použití poskytovatele typu WSDL.</span><span class="sxs-lookup"><span data-stu-id="986a0-119">In the step, you create a project and add the appropriate references to use a WSDL type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="986a0-120">Postup vytvoření a nastavení projektu jazyka F#</span><span class="sxs-lookup"><span data-stu-id="986a0-120">To create and set up an F# project</span></span>

1. <span data-ttu-id="986a0-121">Otevřete nový projekt konzolové aplikace v F #.</span><span class="sxs-lookup"><span data-stu-id="986a0-121">Open a new F# Console Application project.</span></span>
<br />

2. <span data-ttu-id="986a0-122">V **Průzkumníku řešení**, otevřete místní nabídky projektu **odkaz** uzel a potom zvolte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="986a0-122">In **Solution Explorer**, open the shortcut menu for the project's **Reference** node, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="986a0-123">V **sestavení** oblasti, zvolte **Framework**a potom v seznamu dostupných sestavení, zvolte **System.Runtime.Serialization** a  **System.ServiceModel**.</span><span class="sxs-lookup"><span data-stu-id="986a0-123">In the **Assemblies** area, choose **Framework**, and then, in the list of available assemblies, choose **System.Runtime.Serialization** and **System.ServiceModel**.</span></span>
<br />

4. <span data-ttu-id="986a0-124">V **sestavení** oblasti, zvolte **rozšíření**.</span><span class="sxs-lookup"><span data-stu-id="986a0-124">In the **Assemblies** area, choose **Extensions**.</span></span>
<br />

5. <span data-ttu-id="986a0-125">V seznamu dostupných sestavení, zvolte **FSharp.Data.TypeProviders**a potom zvolte **OK** tlačítko přidáte odkazy na tyto sestavení.</span><span class="sxs-lookup"><span data-stu-id="986a0-125">In the list of available assemblies, choose **FSharp.Data.TypeProviders**, and then choose the **OK** button to add references to these assemblies.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="986a0-126">Konfigurace poskytovatele typu</span><span class="sxs-lookup"><span data-stu-id="986a0-126">Configuring the type provider</span></span>
<span data-ttu-id="986a0-127">V tomto kroku použijete ke generování typy pro webovou službu TerraServer WSDL typ zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="986a0-127">In this step, you use the WSDL type provider to generate types for the TerraServer web service.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="986a0-128">Postup konfigurace poskytovatele typu a generování typů</span><span class="sxs-lookup"><span data-stu-id="986a0-128">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="986a0-129">Přidejte následující řádek kódu otevřete obor názvů zprostředkovatele typu.</span><span class="sxs-lookup"><span data-stu-id="986a0-129">Add the following line of code to open the type provider namespace.</span></span>
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. <span data-ttu-id="986a0-130">Přidejte následující řádek kódu pro vyvolání typu zprostředkovatele s webovou službou.</span><span class="sxs-lookup"><span data-stu-id="986a0-130">Add the following line of code to invoke the type provider with a web service.</span></span> <span data-ttu-id="986a0-131">V tomto příkladu použijte TerraServer webové služby.</span><span class="sxs-lookup"><span data-stu-id="986a0-131">In this example, use the TerraServer web service.</span></span>
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "http://terraserver-usa.com/TerraService2.asmx?WSDL" http://msrmaps.com/TerraService2.asmx?WSDL">
```

  <span data-ttu-id="986a0-132">Červenou vlnovkou se zobrazí pod tento řádek kódu URI služby je chybný nebo pokud samotné služby je vypnutý nebo není provádění.</span><span class="sxs-lookup"><span data-stu-id="986a0-132">A red squiggle appears under this line of code if the service URI is misspelled or if the service itself is down or isn’t performing.</span></span> <span data-ttu-id="986a0-133">Pokud zadáte odkaz na kód, chybová zpráva popisuje problém.</span><span class="sxs-lookup"><span data-stu-id="986a0-133">If you point to the code, an error message describes the problem.</span></span> <span data-ttu-id="986a0-134">Stejné informace ve můžete najít **seznam chyb** okno nebo v **výstup – okno** po sestavení.</span><span class="sxs-lookup"><span data-stu-id="986a0-134">You can find the same information in the **Error List** window or in the **Output Window** after you build.</span></span>
<br />  <span data-ttu-id="986a0-135">Existují dva způsoby ke specifikaci nastavení konfigurace pro připojení WSDL pomocí souboru app.config pro projekt nebo pomocí statické typ parametry v deklaraci typu poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="986a0-135">There are two ways to specify configuration settings for a WSDL connection, by using the app.config file for the project, or by using the static type parameters in the type provider declaration.</span></span> <span data-ttu-id="986a0-136">Svcutil.exe můžete použít ke generování souboru příslušné konfigurace – elementy.</span><span class="sxs-lookup"><span data-stu-id="986a0-136">You can use svcutil.exe to generate appropriate configuration file elements.</span></span> <span data-ttu-id="986a0-137">Další informace o používání svcutil.exe generovat informace o konfiguraci pro webové služby najdete v tématu [ServiceModel Metadata Utility Tool &#40; Svcutil.exe &#41; ](https://msdn.microsoft.com/library/aa347733.aspx).</span><span class="sxs-lookup"><span data-stu-id="986a0-137">For more information about using svcutil.exe to generate configuration information for a web service, see [ServiceModel Metadata Utility Tool &#40;Svcutil.exe&#41;](https://msdn.microsoft.com/library/aa347733.aspx).</span></span> <span data-ttu-id="986a0-138">Úplný popis Parametry statické typu pro typ zprostředkovatele WSDL, najdete v části [wsdlservice – zprostředkovatel typu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="986a0-138">For a full description of the static type parameters for the WSDL type provider, see [WsdlService Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).</span></span>
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a><span data-ttu-id="986a0-139">Volání webové služby a zpracování výsledků</span><span class="sxs-lookup"><span data-stu-id="986a0-139">Calling the web service, and processing the results</span></span>
<span data-ttu-id="986a0-140">Každý webová služba má vlastní sadu typů, které jsou použity jako parametry pro jeho volání metody.</span><span class="sxs-lookup"><span data-stu-id="986a0-140">Each web service has its own set of types that are used as parameters for its method calls.</span></span> <span data-ttu-id="986a0-141">V tomto kroku připravit tyto parametry, volání metody webové a zpracovat informace, které vrátí.</span><span class="sxs-lookup"><span data-stu-id="986a0-141">In this step, you prepare these parameters, call a web method, and process the information that it returns.</span></span>


#### <a name="to-call-the-web-service-and-process-the-results"></a><span data-ttu-id="986a0-142">Volání webové služby a zpracovat výsledky</span><span class="sxs-lookup"><span data-stu-id="986a0-142">To call the web service, and process the results</span></span>

1. <span data-ttu-id="986a0-143">Webová služba může vypršení časového limitu nebo přestane fungovat, takže by měla obsahovat volání webové služby v bloku zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="986a0-143">The web service might time out or stop functioning, so you should include the web service call in an exception handling block.</span></span> <span data-ttu-id="986a0-144">Následující kód pokusit se získat data z webové služby zápisu.</span><span class="sxs-lookup"><span data-stu-id="986a0-144">Write the following code to try to get data from the web service.</span></span>
<br />

```fsharp
try
  let terraClient = TerraService.GetTerraServiceSoap ()
  let myPlace = new TerraService.ServiceTypes.msrmaps.com.Place(City = "Redmond", State = "Washington", Country = "United States")
  let myLocation = terraClient.ConvertPlaceToLonLatPt(myPlace)
  printfn "Redmond Latitude: %f Longitude: %f" (myLocation.Lat) (myLocation.Lon)
with
| :? ServerTooBusyException as exn ->
  let innerMessage =
    match (exn.InnerException) with
    | null -> ""
    | innerExn -> innerExn.Message
  printfn "An exception occurred:\n %s\n %s" exn.Message innerMessage
| exn -> printfn "An exception occurred: %s" exn.Message
```

<span data-ttu-id="986a0-145">Všimněte si, že můžete vytvořit datové typy, které jsou potřebné pro webovou službu, jako například **místní** a **umístění**, jako typ vnořené typy pod wsdlservice – **TerraService**.</span><span class="sxs-lookup"><span data-stu-id="986a0-145">Notice that you create the data types that are needed for the web service, such as **Place** and **Location**, as nested types under the WsdlService type **TerraService**.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="986a0-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="986a0-146">See Also</span></span>
[<span data-ttu-id="986a0-147">Wsdlservice – zprostředkovatel typu</span><span class="sxs-lookup"><span data-stu-id="986a0-147">WsdlService Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[<span data-ttu-id="986a0-148">Zprostředkovatelé typů</span><span class="sxs-lookup"><span data-stu-id="986a0-148">Type Providers</span></span>](index.md)

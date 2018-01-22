---
title: "Postupy: ruční generují třídy služby dat klienta (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dba117ac9f4fd7dc745019d9705c2a707a5b526c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="31f78-102">Postupy: ruční generují třídy služby dat klienta (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="31f78-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="31f78-103">se integruje s Visual Studio umožňují automaticky generovat třídy služeb klienta data při použití **přidat odkaz na službu** dialogové okno Přidat odkaz na datové služby v projektu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31f78-103"> integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="31f78-104">Další informace najdete v tématu [postupy: Přidání odkazu na službu Data](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="31f78-104">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="31f78-105">Stejné třídy služby dat klienta lze vytvořit také ručně pomocí nástroje generování kódu `DataSvcUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="31f78-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="31f78-106">Tento nástroj, který je součástí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vygeneruje třídy rozhraní .NET Framework z definici datové služby.</span><span class="sxs-lookup"><span data-stu-id="31f78-106">This tool, which is included with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="31f78-107">Také se použít pro generování třídy služeb dat ze souboru konceptuálního modelu (.csdl) a ze souboru .edmx, který představuje model Entity Framework v projektu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31f78-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>  
  
 <span data-ttu-id="31f78-108">V příkladu v tomto tématu se vytvoří třídy služeb dat klienta založené na službě Northwind ukázková data.</span><span class="sxs-lookup"><span data-stu-id="31f78-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="31f78-109">Tato služba se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="31f78-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="31f78-110">Některé příklady v tomto tématu vyžadují soubor konceptuálního modelu pro Northwind model.</span><span class="sxs-lookup"><span data-stu-id="31f78-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="31f78-111">Další informace najdete v tématu [postupy: použití EdmGen.exe pro generování modelu a mapování soubory](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="31f78-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="31f78-112">Některé příklady v tomto tématu vyžadují soubor EDMX Northwind modelu.</span><span class="sxs-lookup"><span data-stu-id="31f78-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="31f78-113">Další informace najdete v tématu [.edmx souboru přehled](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span><span class="sxs-lookup"><span data-stu-id="31f78-113">For more information, see [.edmx File Overview](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span></span>  
  
### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="31f78-114">Vygenerovat třídy jazyka C#, které podporují datová vazba</span><span class="sxs-lookup"><span data-stu-id="31f78-114">To generate C# classes that support data binding</span></span>  
  
-   <span data-ttu-id="31f78-115">Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:</span><span class="sxs-lookup"><span data-stu-id="31f78-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="31f78-116">Hodnota zadaná pro musí nahradit `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.</span><span class="sxs-lookup"><span data-stu-id="31f78-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="31f78-117">Vygenerovat třídy jazyka Visual Basic, které podporují datová vazba</span><span class="sxs-lookup"><span data-stu-id="31f78-117">To generate Visual Basic classes that support data binding</span></span>  
  
-   <span data-ttu-id="31f78-118">Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:</span><span class="sxs-lookup"><span data-stu-id="31f78-118">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="31f78-119">Hodnota zadaná pro musí nahradit `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.</span><span class="sxs-lookup"><span data-stu-id="31f78-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="31f78-120">Vygenerovat C# třídy založené na URI služby</span><span class="sxs-lookup"><span data-stu-id="31f78-120">To generate C# classes based on the service URI</span></span>  
  
-   <span data-ttu-id="31f78-121">Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:</span><span class="sxs-lookup"><span data-stu-id="31f78-121">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="31f78-122">Hodnota zadaná pro musí nahradit `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.</span><span class="sxs-lookup"><span data-stu-id="31f78-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="31f78-123">Vygenerovat URI služby podle třídy jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31f78-123">To generate Visual Basic classes based on the service URI</span></span>  
  
-   <span data-ttu-id="31f78-124">Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:</span><span class="sxs-lookup"><span data-stu-id="31f78-124">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="31f78-125">Hodnota zadaná pro musí nahradit `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.</span><span class="sxs-lookup"><span data-stu-id="31f78-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="31f78-126">Ke generování třídy jazyka C# na základě souboru konceptuálního modelu (CSDL)</span><span class="sxs-lookup"><span data-stu-id="31f78-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>  
  
-   <span data-ttu-id="31f78-127">Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:</span><span class="sxs-lookup"><span data-stu-id="31f78-127">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs  
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="31f78-128">Vygenerovat na základě souboru konceptuálního modelu (CSDL) třídy jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31f78-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>  
  
-   <span data-ttu-id="31f78-129">Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:</span><span class="sxs-lookup"><span data-stu-id="31f78-129">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb  
    ```  
  
### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="31f78-130">Ke generování třídy jazyka C# na základě souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="31f78-130">To generate C# classes based on the .edmx file</span></span>  
  
-   <span data-ttu-id="31f78-131">Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:</span><span class="sxs-lookup"><span data-stu-id="31f78-131">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs   
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="31f78-132">Vygenerovat na základě souboru .edmx třídy jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31f78-132">To generate Visual Basic classes based on the .edmx file</span></span>  
  
-   <span data-ttu-id="31f78-133">Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:</span><span class="sxs-lookup"><span data-stu-id="31f78-133">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="31f78-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="31f78-134">See Also</span></span>  
 [<span data-ttu-id="31f78-135">Generování klientské knihovny datové služby</span><span class="sxs-lookup"><span data-stu-id="31f78-135">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [<span data-ttu-id="31f78-136">Postupy: Přidání odkazu na datovou službu</span><span class="sxs-lookup"><span data-stu-id="31f78-136">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)  
 [<span data-ttu-id="31f78-137">Nástroj klienta WCF Data Services (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="31f78-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)

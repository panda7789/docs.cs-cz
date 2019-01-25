---
title: 'Postupy: Ruční generování tříd klientské datové služby (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: c95ad9371854257059861b7d1e48c7afbc957ea1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613227"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="5f36c-102">Postupy: Ruční generování tříd klientské datové služby (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="5f36c-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
<span data-ttu-id="5f36c-103">Služeb WCF Data Services se integruje se sadou Visual Studio umožňuje automatické generování tříd klientské datové služby, pokud použijete **přidat odkaz na službu** dialogové okno Přidat odkaz na datovou službu v projektu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f36c-103">WCF Data Services integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="5f36c-104">Další informace najdete v tématu [jak: Přidání odkazu na datovou službu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="5f36c-104">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="5f36c-105">Můžete také ručně generovat stejný tříd klientské datové služby pomocí nástroje pro generování kódu, `DataSvcUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="5f36c-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="5f36c-106">Tento nástroj, který je součástí služeb WCF Data Services, vygeneruje třídy rozhraní .NET Framework v definici datové služby.</span><span class="sxs-lookup"><span data-stu-id="5f36c-106">This tool, which is included with WCF Data Services, generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="5f36c-107">Je také slouží ke generování třídy služeb data ze souboru koncepčního modelu (.csdl) a ze souboru EDMX, který představuje model Entity Framework v projektu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f36c-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>

 <span data-ttu-id="5f36c-108">V příkladu v tomto tématu se vytvoří tříd klientské datové služby založené na vzorku datová služba Northwind.</span><span class="sxs-lookup"><span data-stu-id="5f36c-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="5f36c-109">Tato služba se vytvoří při dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="5f36c-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="5f36c-110">Příklady v tomto tématu vyžadují souboru koncepčního modelu pro Northwind model.</span><span class="sxs-lookup"><span data-stu-id="5f36c-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="5f36c-111">Další informace najdete v tématu [jak: Použití EdmGen.exe pro generování modelu a souborů mapování](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="5f36c-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="5f36c-112">Příklady v tomto tématu vyžadují soubor .edmx pro Northwind model.</span><span class="sxs-lookup"><span data-stu-id="5f36c-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="5f36c-113">Další informace najdete v tématu [edmx soubor přehled](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span><span class="sxs-lookup"><span data-stu-id="5f36c-113">For more information, see [.edmx File Overview](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span></span>

### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="5f36c-114">Ke generování třídy jazyka C#, které podporují vytváření datových vazeb</span><span class="sxs-lookup"><span data-stu-id="5f36c-114">To generate C# classes that support data binding</span></span>

-   <span data-ttu-id="5f36c-115">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="5f36c-115">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="5f36c-116">Je třeba nahradit hodnota předaná `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.</span><span class="sxs-lookup"><span data-stu-id="5f36c-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="5f36c-117">Ke generování třídy jazyka Visual Basic, které podporují vytváření datových vazeb</span><span class="sxs-lookup"><span data-stu-id="5f36c-117">To generate Visual Basic classes that support data binding</span></span>

-   <span data-ttu-id="5f36c-118">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="5f36c-118">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="5f36c-119">Je třeba nahradit hodnota předaná `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.</span><span class="sxs-lookup"><span data-stu-id="5f36c-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="5f36c-120">Ke generování třídy jazyka C# založeny na identifikátor URI služby</span><span class="sxs-lookup"><span data-stu-id="5f36c-120">To generate C# classes based on the service URI</span></span>

-   <span data-ttu-id="5f36c-121">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="5f36c-121">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="5f36c-122">Je třeba nahradit hodnota předaná `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.</span><span class="sxs-lookup"><span data-stu-id="5f36c-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="5f36c-123">Ke generování třídy jazyka Visual Basic založené na identifikátor URI služby</span><span class="sxs-lookup"><span data-stu-id="5f36c-123">To generate Visual Basic classes based on the service URI</span></span>

-   <span data-ttu-id="5f36c-124">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="5f36c-124">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="5f36c-125">Je třeba nahradit hodnota předaná `/uri:` parametr s identifikátorem URI vaší instance služby Northwind ukázková data.</span><span class="sxs-lookup"><span data-stu-id="5f36c-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="5f36c-126">Ke generování třídy jazyka C# založeny na souboru koncepčního modelu (CSDL)</span><span class="sxs-lookup"><span data-stu-id="5f36c-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>

-   <span data-ttu-id="5f36c-127">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="5f36c-127">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="5f36c-128">Ke generování třídy jazyka Visual Basic konceptuálního modelu souboru (CSDL)</span><span class="sxs-lookup"><span data-stu-id="5f36c-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>

-   <span data-ttu-id="5f36c-129">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="5f36c-129">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="5f36c-130">Ke generování třídy jazyka C# na základě souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="5f36c-130">To generate C# classes based on the .edmx file</span></span>

-   <span data-ttu-id="5f36c-131">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="5f36c-131">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="5f36c-132">Ke generování třídy jazyka Visual Basic na základě souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="5f36c-132">To generate Visual Basic classes based on the .edmx file</span></span>

-   <span data-ttu-id="5f36c-133">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="5f36c-133">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a><span data-ttu-id="5f36c-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f36c-134">See also</span></span>

- [<span data-ttu-id="5f36c-135">Generování klientské knihovny datové služby</span><span class="sxs-lookup"><span data-stu-id="5f36c-135">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="5f36c-136">Postupy: Přidání odkazu na datovou službu</span><span class="sxs-lookup"><span data-stu-id="5f36c-136">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
- [<span data-ttu-id="5f36c-137">Nástroj klienta WCF Data Services (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="5f36c-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
---
title: 'Postupy: Ruční generování tříd klientských datových služeb (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: f8d99213a1ef98c48855ba9f561f87a800768c89
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894294"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="3dd63-102">Postupy: Ruční generování tříd klientských datových služeb (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="3dd63-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
<span data-ttu-id="3dd63-103">WCF Data Services se integruje se sadou Visual Studio, aby vám umožnila automatické generování tříd klientské datové služby při použití dialogového okna **Přidat odkaz na službu** k přidání odkazu na datovou službu v projektu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3dd63-103">WCF Data Services integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="3dd63-104">Další informace najdete v tématu [jak: Přidejte odkaz](how-to-add-a-data-service-reference-wcf-data-services.md)na datovou službu.</span><span class="sxs-lookup"><span data-stu-id="3dd63-104">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="3dd63-105">Můžete také ručně vygenerovat stejné třídy datové služby klienta pomocí nástroje `DataSvcUtil.exe`pro generování kódu.</span><span class="sxs-lookup"><span data-stu-id="3dd63-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="3dd63-106">Tento nástroj, který je součástí WCF Data Services, generuje .NET Framework třídy z definice datové služby.</span><span class="sxs-lookup"><span data-stu-id="3dd63-106">This tool, which is included with WCF Data Services, generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="3dd63-107">Lze ji také použít ke generování tříd datové služby ze souboru koncepčního modelu (. CSDL) a ze souboru. edmx, který představuje model Entity Framework v projektu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3dd63-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>

 <span data-ttu-id="3dd63-108">Příklad v tomto tématu vytvoří klientské třídy datové služby založené na ukázkové datové službě Northwind.</span><span class="sxs-lookup"><span data-stu-id="3dd63-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="3dd63-109">Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="3dd63-109">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="3dd63-110">Některé příklady v tomto tématu vyžadují koncepční soubor modelu pro model Northwind.</span><span class="sxs-lookup"><span data-stu-id="3dd63-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="3dd63-111">Další informace najdete v tématu [jak: K vygenerování modelu a mapování souborů](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)použijte EdmGen. exe.</span><span class="sxs-lookup"><span data-stu-id="3dd63-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="3dd63-112">Některé příklady v tomto tématu vyžadují soubor. edmx pro model Northwind.</span><span class="sxs-lookup"><span data-stu-id="3dd63-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="3dd63-113">Další informace najdete v tématu [Přehled souborů. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3dd63-113">For more information, see [.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span></span>

### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="3dd63-114">Generovat C# třídy, které podporují datové vazby</span><span class="sxs-lookup"><span data-stu-id="3dd63-114">To generate C# classes that support data binding</span></span>

- <span data-ttu-id="3dd63-115">Na příkazovém řádku spusťte následující příkaz bez konců řádků:</span><span class="sxs-lookup"><span data-stu-id="3dd63-115">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="3dd63-116">Je nutné nahradit hodnotu `/uri:` dodanou parametr identifikátorem URI vaší instance služby ukázkových dat Northwind.</span><span class="sxs-lookup"><span data-stu-id="3dd63-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="3dd63-117">Generování Visual Basic třídy, které podporují datové vazby</span><span class="sxs-lookup"><span data-stu-id="3dd63-117">To generate Visual Basic classes that support data binding</span></span>

- <span data-ttu-id="3dd63-118">Na příkazovém řádku spusťte následující příkaz bez konců řádků:</span><span class="sxs-lookup"><span data-stu-id="3dd63-118">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="3dd63-119">Je nutné nahradit hodnotu dodanou `/uri:` parametr identifikátorem URI vaší instance služby ukázkových dat Northwind.</span><span class="sxs-lookup"><span data-stu-id="3dd63-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="3dd63-120">Generování C# tříd založených na identifikátoru URI služby</span><span class="sxs-lookup"><span data-stu-id="3dd63-120">To generate C# classes based on the service URI</span></span>

- <span data-ttu-id="3dd63-121">Na příkazovém řádku spusťte následující příkaz bez konců řádků:</span><span class="sxs-lookup"><span data-stu-id="3dd63-121">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="3dd63-122">Je nutné nahradit hodnotu `/uri:` dodanou parametr identifikátorem URI vaší instance služby ukázkových dat Northwind.</span><span class="sxs-lookup"><span data-stu-id="3dd63-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="3dd63-123">Generování tříd Visual Basic na základě identifikátoru URI služby</span><span class="sxs-lookup"><span data-stu-id="3dd63-123">To generate Visual Basic classes based on the service URI</span></span>

- <span data-ttu-id="3dd63-124">Na příkazovém řádku spusťte následující příkaz bez konců řádků:</span><span class="sxs-lookup"><span data-stu-id="3dd63-124">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="3dd63-125">Je nutné nahradit hodnotu dodanou `/uri:` parametr identifikátorem URI vaší instance služby ukázkových dat Northwind.</span><span class="sxs-lookup"><span data-stu-id="3dd63-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="3dd63-126">Generování C# tříd založených na souboru koncepčního modelu (CSDL)</span><span class="sxs-lookup"><span data-stu-id="3dd63-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="3dd63-127">Na příkazovém řádku spusťte následující příkaz bez konců řádků:</span><span class="sxs-lookup"><span data-stu-id="3dd63-127">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="3dd63-128">Vygenerování Visual Basic třídy založené na souboru koncepčního modelu (CSDL)</span><span class="sxs-lookup"><span data-stu-id="3dd63-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="3dd63-129">Na příkazovém řádku spusťte následující příkaz bez konců řádků:</span><span class="sxs-lookup"><span data-stu-id="3dd63-129">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="3dd63-130">Generování C# tříd založených na souboru. edmx</span><span class="sxs-lookup"><span data-stu-id="3dd63-130">To generate C# classes based on the .edmx file</span></span>

- <span data-ttu-id="3dd63-131">Na příkazovém řádku spusťte následující příkaz bez konců řádků:</span><span class="sxs-lookup"><span data-stu-id="3dd63-131">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="3dd63-132">Generování Visual Basic tříd založených na souboru. edmx</span><span class="sxs-lookup"><span data-stu-id="3dd63-132">To generate Visual Basic classes based on the .edmx file</span></span>

- <span data-ttu-id="3dd63-133">Na příkazovém řádku spusťte následující příkaz bez konců řádků:</span><span class="sxs-lookup"><span data-stu-id="3dd63-133">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a><span data-ttu-id="3dd63-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3dd63-134">See also</span></span>

- [<span data-ttu-id="3dd63-135">Generování klientské knihovny datové služby</span><span class="sxs-lookup"><span data-stu-id="3dd63-135">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="3dd63-136">Postupy: Přidat odkaz na datovou službu</span><span class="sxs-lookup"><span data-stu-id="3dd63-136">How to: Add a Data Service Reference</span></span>](how-to-add-a-data-service-reference-wcf-data-services.md)
- [<span data-ttu-id="3dd63-137">Nástroj klienta WCF Data Services (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="3dd63-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](wcf-data-service-client-utility-datasvcutil-exe.md)

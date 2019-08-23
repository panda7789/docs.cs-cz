---
title: Ukázka technologie serializace obecných typů ve webových službách
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 467bfe1fd9eb8a0222385c34cb29a90df00dc937
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960752"
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="bfb4e-102">Ukázka technologie serializace obecných typů ve webových službách</span><span class="sxs-lookup"><span data-stu-id="bfb4e-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="bfb4e-103">Ukázka stažení</span><span class="sxs-lookup"><span data-stu-id="bfb4e-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="bfb4e-104">Tento příklad ukazuje, jak používat a řídit serializaci generických typů v ASP.NET webových službách.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="bfb4e-105">K vytvoření vzorku pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bfb4e-105">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="bfb4e-106">Otevřete Visual Studio a v nabídce **soubor** vyberte **Nový web** .</span><span class="sxs-lookup"><span data-stu-id="bfb4e-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2. <span data-ttu-id="bfb4e-107">V dialogovém okně **Nový web** vyberte v levém podokně požadovaný programovací jazyk a potom v pravém podokně vyberte **ASP.NET webová služba**.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3. <span data-ttu-id="bfb4e-108">Klikněte na **Procházet** a přejděte do podadresáře \CS\GenericsService.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4. <span data-ttu-id="bfb4e-109">Vyberte Service.asmx k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5. <span data-ttu-id="bfb4e-110">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bfb4e-111">Prvních pět kroků v tomto seznamu jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="bfb4e-112">Modul runtime rozhraní .NET Framework, bude automaticky generovat webové služby první čas, kdy je požadována služba.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bfb4e-113">Následující kroky jsou nutné k vytvoření vzorku.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-113">The following steps are required to build the sample.</span></span>  
  
1. <span data-ttu-id="bfb4e-114">Otevřete Průzkumníka souborů a přejděte do podadresáře \CS.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-114">Open File Explorer and navigate to the \CS subdirectory.</span></span>  
  
2. <span data-ttu-id="bfb4e-115">Klikněte pravým tlačítkem na ikonu podadresáře GenericsService a vyberte **sdílení a zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3. <span data-ttu-id="bfb4e-116">Na kartě **sdílení webu** vyberte **sdílet tuto složku**.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bfb4e-117">Poznamenejte si název virtuálního adresáře, který je uvedený v podokně **aliasy** , protože ho budete potřebovat ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="bfb4e-118">K vytvoření vzorku pomocí Internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="bfb4e-118">To build the sample using Internet Information Services</span></span>  
  
1. <span data-ttu-id="bfb4e-119">Otevřete modul snap-in Správa **Internetová informační služba** a rozbalte **weby**.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2. <span data-ttu-id="bfb4e-120">Klikněte levým na **výchozí web**, vyberte **Nový**a potom vyberte **virtuální adresář?** a vytvořte tak **Průvodce vytvořením virtuálního adresáře**.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3. <span data-ttu-id="bfb4e-121">Klikněte na **Další**, zadejte veřejný alias pro virtuální adresář a klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4. <span data-ttu-id="bfb4e-122">Zadejte cestu k adresáři, do kterého jste ukázku uložili (obvykle podadresář \CS\GenericsService), a klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="bfb4e-123">Průvodce dokončíte kliknutím na tlačítko **Další** .</span><span class="sxs-lookup"><span data-stu-id="bfb4e-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bfb4e-124">Poznamenejte si název virtuálního adresáře, který je uvedený v podokně **alias** , protože ho budete potřebovat ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="bfb4e-125">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="bfb4e-125">To run the sample</span></span>  
  
1. <span data-ttu-id="bfb4e-126">Otevřete okno prohlížeče a vyberte jeho adresa.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-126">Open a browser window and select its address bar.</span></span>  
  
2. <span data-ttu-id="bfb4e-127">Typ `http://localhost/[virtual directory]/Service.asmx`, kde `[virtual directory]` představuje virtuální adresář, který jste vytvořili při vytvoření ukázky.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-127">Type `http://localhost/[virtual directory]/Service.asmx`, where `[virtual directory]` represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfb4e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bfb4e-128">Remarks</span></span>  
 <span data-ttu-id="bfb4e-129">Ukázka zobrazí výchozí stránka technologie ASP.NET, která obsahuje odkazy na definice webové služby.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="bfb4e-130">Můžete přizpůsobit zobrazení kromě Změna zdrojového kódu webové služby.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="bfb4e-131">Další informace naleznete v tématu [sestavování klientů webové služby XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bfb4e-131">For more information, see [Building XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb4e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bfb4e-132">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [<span data-ttu-id="bfb4e-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="bfb4e-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- <span data-ttu-id="bfb4e-134">[Webové služby XML vytvořené pomocí ASP.NET a klientů webové služby XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bfb4e-134">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>

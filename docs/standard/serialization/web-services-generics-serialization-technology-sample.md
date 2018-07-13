---
title: Ukázka technologie serializace obecných typů služby webového
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 799206b1bd86e98c87441771174441d07074a325
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936773"
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="74ae2-102">Ukázka technologie serializace obecných typů služby webového</span><span class="sxs-lookup"><span data-stu-id="74ae2-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="74ae2-103">Stáhněte si ukázky</span><span class="sxs-lookup"><span data-stu-id="74ae2-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="74ae2-104">Tento příklad ukazuje, jak používat a řídit serializace obecných typů v webové služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="74ae2-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="74ae2-105">K vytvoření vzorku pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="74ae2-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="74ae2-106">Otevřít Visual Studio a vyberte **nový web** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="74ae2-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="74ae2-107">V **nový web** dialogového okna, vyberte v levém podokně požadovanou programovací jazyk a potom v pravém podokně vyberte **webová služba ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="74ae2-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="74ae2-108">Klikněte na tlačítko **Procházet** a přejděte do podadresáře \CS\GenericsService.</span><span class="sxs-lookup"><span data-stu-id="74ae2-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4.  <span data-ttu-id="74ae2-109">Vyberte Service.asmx k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="74ae2-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5.  <span data-ttu-id="74ae2-110">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="74ae2-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74ae2-111">Prvních pět kroků v tomto seznamu jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="74ae2-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="74ae2-112">Modul runtime rozhraní .NET Framework, bude automaticky generovat webové služby první čas, kdy je požadována služba.</span><span class="sxs-lookup"><span data-stu-id="74ae2-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74ae2-113">Následující kroky jsou nutné k vytvoření vzorku.</span><span class="sxs-lookup"><span data-stu-id="74ae2-113">The following steps are required to build the sample.</span></span>  
  
1.  <span data-ttu-id="74ae2-114">Otevřít [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] a přejděte do podadresáře \CS.</span><span class="sxs-lookup"><span data-stu-id="74ae2-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the \CS subdirectory.</span></span>  
  
2.  <span data-ttu-id="74ae2-115">Klikněte pravým tlačítkem na ikonu podadresáři GenericsService a vyberte **sdílení a zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="74ae2-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3.  <span data-ttu-id="74ae2-116">V **sdílení na webu** kartu, vyberte možnost **sdílet tuto složku**.</span><span class="sxs-lookup"><span data-stu-id="74ae2-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74ae2-117">Poznamenejte si název virtuálního adresáře, který je uveden v **aliasy** podokno, protože je budete potřebovat ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="74ae2-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="74ae2-118">K vytvoření vzorku pomocí Internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="74ae2-118">To build the sample using Internet Information Services</span></span>  
  
1.  <span data-ttu-id="74ae2-119">Otevřít **Internetová informační služba** správy modulu snap-in a rozbalení **weby**.</span><span class="sxs-lookup"><span data-stu-id="74ae2-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2.  <span data-ttu-id="74ae2-120">Klepněte na položku **výchozí webový server**vyberte **nový**a pak vyberte **virtuální adresář?** vytvořit **Průvodce vytvořením virtuálního adresáře**.</span><span class="sxs-lookup"><span data-stu-id="74ae2-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3.  <span data-ttu-id="74ae2-121">Klikněte na tlačítko **Další**, zadejte veřejné alias pro virtuální adresář a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="74ae2-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="74ae2-122">Zadejte cestu k adresáři, kam jste uložili vzorku (obvykle podadresář \CS\GenericsService) a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="74ae2-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="74ae2-123">Klikněte na tlačítko **Další** dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="74ae2-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74ae2-124">Poznamenejte si název virtuálního adresáře, který je uveden v **Alias** podokno, protože je budete potřebovat ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="74ae2-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="74ae2-125">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="74ae2-125">To run the sample</span></span>  
  
1.  <span data-ttu-id="74ae2-126">Otevřete okno prohlížeče a vyberte jeho adresa.</span><span class="sxs-lookup"><span data-stu-id="74ae2-126">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="74ae2-127">Typ `http://localhost/[virtual directory]/Service.asmx`, kde `[virtual directory]` představuje virtuální adresář, který jste vytvořili při sestavení vzorku.</span><span class="sxs-lookup"><span data-stu-id="74ae2-127">Type `http://localhost/[virtual directory]/Service.asmx`, where `[virtual directory]` represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74ae2-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74ae2-128">Remarks</span></span>  
 <span data-ttu-id="74ae2-129">Ukázka zobrazí výchozí stránka technologie ASP.NET, která obsahuje odkazy na definice webové služby.</span><span class="sxs-lookup"><span data-stu-id="74ae2-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="74ae2-130">Můžete přizpůsobit zobrazení kromě Změna zdrojového kódu webové služby.</span><span class="sxs-lookup"><span data-stu-id="74ae2-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="74ae2-131">Další informace najdete v tématu [klienty vytváření XML webové služby](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).</span><span class="sxs-lookup"><span data-stu-id="74ae2-131">For more information, see [Building XML Web Service Clients](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ae2-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="74ae2-132">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Web.Services>  
 <xref:System.Xml.Serialization>  
 [<span data-ttu-id="74ae2-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="74ae2-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="74ae2-134">Webové služby XML vytvořené pomocí ASP.NET a klienty webové služby XML</span><span class="sxs-lookup"><span data-stu-id="74ae2-134">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)

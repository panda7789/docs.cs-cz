---
title: Ukázka IXmlSerializable technologie webové služby
ms.date: 03/30/2017
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
ms.openlocfilehash: eb117f720e7541ac6460b5adfd0eecc7901f4fdf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582711"
---
# <a name="web-services-ixmlserializable-technology-sample"></a><span data-ttu-id="c5038-102">Ukázka IXmlSerializable technologie webové služby</span><span class="sxs-lookup"><span data-stu-id="c5038-102">Web Services IXmlSerializable Technology Sample</span></span>
[<span data-ttu-id="c5038-103">Stažení ukázky</span><span class="sxs-lookup"><span data-stu-id="c5038-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 <span data-ttu-id="c5038-104">Tento příklad ukazuje, jak používat <xref:System.Xml.Serialization.IXmlSerializable> k řízení serializace vlastních typů ve webové služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c5038-104">This sample shows how to use <xref:System.Xml.Serialization.IXmlSerializable> to control the serialization of custom types in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="c5038-105">K vytvoření vzorku pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c5038-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="c5038-106">Otevřete [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] a vyberte **nový web** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c5038-106">Open [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="c5038-107">V levém podokně **nový web** dialogovém okně, vyberte požadovaný programovací jazyk a pak v pravém podokně vyberte **webovou službu ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="c5038-107">In the left pane of the **New Web Site** dialog, select your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="c5038-108">Typ **IXmlSerializable** jako název nové webové služby.</span><span class="sxs-lookup"><span data-stu-id="c5038-108">Type **IXmlSerializable** as the name of the new Web service.</span></span>  
  
4.  <span data-ttu-id="c5038-109">V okně Průzkumníku řešení klikněte pravým tlačítkem na ikonu pro Service.asmx a vyberte **odstranit**; tento krok opakujte pro soubor codebehind Service.asmx.</span><span class="sxs-lookup"><span data-stu-id="c5038-109">In the Solution Explorer window, right-click the icon for Service.asmx and select **Delete**; repeat this step for the Service.asmx codebehind file.</span></span>  
  
5.  <span data-ttu-id="c5038-110">Klikněte pravým tlačítkem na projekt adresář a zaškrtněte možnost **přidat existující položku**.</span><span class="sxs-lookup"><span data-stu-id="c5038-110">Right-click the project directory and select **Add Existing Item**.</span></span> <span data-ttu-id="c5038-111">V dialogovém okně přejděte na podadresáři služby adresáře konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="c5038-111">In the dialog, navigate to the Service subdirectory of the language-specific directory.</span></span>  
  
6.  <span data-ttu-id="c5038-112">Vyberte Service.asmx a poté opakujte tento krok pro soubor codebehind Service.asmx.</span><span class="sxs-lookup"><span data-stu-id="c5038-112">Select Service.asmx, then repeat this step for the Service.asmx codebehind file.</span></span>  
  
7.  <span data-ttu-id="c5038-113">Otevřít [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] a přejděte do adresáře, který obsahuje IXmlSerializable adresář, který jste vytvořili v kroku 3 výše.</span><span class="sxs-lookup"><span data-stu-id="c5038-113">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the directory that contains IXmlSerializable directory that you created in step 3 above.</span></span>  
  
8.  <span data-ttu-id="c5038-114">Klikněte pravým tlačítkem myši na ikonu pro IXmlSerializable adresář a vyberte **sdílení a zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="c5038-114">Right-click the icon for the IXmlSerializable directory and select **Sharing and Security**.</span></span>  
  
9. <span data-ttu-id="c5038-115">Na kartě Sdílení na webu vyberte **Sdílejte tuto složku**a potvrďte výchozí nastavení, včetně názvu IXmlSerializable.</span><span class="sxs-lookup"><span data-stu-id="c5038-115">In the Web Sharing tab, select **Share this Folder**, and confirm the default settings, including the name IXmlSerializable.</span></span>  
  
10. <span data-ttu-id="c5038-116">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5038-116">Click **OK**.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="c5038-117">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="c5038-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="c5038-118">Otevřete okno prohlížeče a vyberte jeho adresa.</span><span class="sxs-lookup"><span data-stu-id="c5038-118">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="c5038-119">Typ **http://localhost/IXmlSerializable/Service.asmx**.</span><span class="sxs-lookup"><span data-stu-id="c5038-119">Type **http://localhost/IXmlSerializable/Service.asmx**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5038-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5038-120">See Also</span></span>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization>  
 <xref:System.Xml.XmlConvert>  
 <xref:System.Xml.XmlQualifiedName>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.XmlSchema>  
 <xref:System.Xml.Schema.XmlSchemaSet>  
 <xref:System.Xml.XmlUrlResolver>  
 <xref:System.Xml.XmlWriter>

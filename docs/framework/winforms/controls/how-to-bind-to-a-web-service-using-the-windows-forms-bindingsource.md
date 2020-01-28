---
title: Vytvoření vazby na webovou službu pomocí objektu BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
ms.openlocfilehash: 0680c73e578577cf40158761f6c635fe30ff9f4d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746682"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="aabc3-102">Postupy: Připojení k webové službě pomocí Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="aabc3-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="aabc3-103">Chcete-li navazovat ovládací prvek Windows Form na výsledky získané z volání webové služby XML, můžete použít komponentu <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="aabc3-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="aabc3-104">Tento postup je podobný jako vytvoření vazby <xref:System.Windows.Forms.BindingSource> komponenty na typ.</span><span class="sxs-lookup"><span data-stu-id="aabc3-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="aabc3-105">Musíte vytvořit proxy server na straně klienta, který obsahuje metody a typy zveřejněné webovou službou.</span><span class="sxs-lookup"><span data-stu-id="aabc3-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="aabc3-106">Vygenerujete proxy server na straně klienta z samotné webové služby (. asmx) nebo z jeho souboru WSDL (Web Services Description Language).</span><span class="sxs-lookup"><span data-stu-id="aabc3-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="aabc3-107">Kromě toho musí proxy server na straně klienta zveřejnit pole komplexních typů, které webová služba používá jako veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aabc3-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="aabc3-108">Potom svážete <xref:System.Windows.Forms.BindingSource> k jednomu z typů zveřejněných v proxy webové služby.</span><span class="sxs-lookup"><span data-stu-id="aabc3-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="aabc3-109">Vytvoření vazby na proxy server na straně klienta</span><span class="sxs-lookup"><span data-stu-id="aabc3-109">To create and bind to a client-side proxy</span></span>  
  
1. <span data-ttu-id="aabc3-110">Vytvořte formulář Windows v adresáři dle vašeho výběru s odpovídajícím oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="aabc3-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2. <span data-ttu-id="aabc3-111">Přidejte do formuláře komponentu <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="aabc3-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3. <span data-ttu-id="aabc3-112">Otevřete příkazový řádek sady Windows Software Development Kit (SDK) a přejděte do stejného adresáře, ve kterém se nachází formulář.</span><span class="sxs-lookup"><span data-stu-id="aabc3-112">Open the Windows Software Development Kit (SDK) command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4. <span data-ttu-id="aabc3-113">Pomocí nástroje WSDL zadejte `wsdl` a adresu URL pro soubor. asmx nebo WSDL pro webovou službu, za kterou následuje obor názvů vaší aplikace, a volitelně i jazyk, ve kterém pracujete.</span><span class="sxs-lookup"><span data-stu-id="aabc3-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="aabc3-114">Následující příklad kódu používá webovou službu, která se nachází na `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span><span class="sxs-lookup"><span data-stu-id="aabc3-114">The following code example uses the Web service located at `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span></span> <span data-ttu-id="aabc3-115">Například pro C# typ `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`nebo pro Visual Basic typu `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span><span class="sxs-lookup"><span data-stu-id="aabc3-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="aabc3-116">Předání cesty jako argumentu nástroje WSDL vygeneruje proxy na straně klienta ve stejném adresáři a oboru názvů jako vaše aplikace v zadaném jazyce.</span><span class="sxs-lookup"><span data-stu-id="aabc3-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="aabc3-117">Pokud používáte aplikaci Visual Studio, přidejte soubor do projektu.</span><span class="sxs-lookup"><span data-stu-id="aabc3-117">If you are using Visual Studio, add the file to your project.</span></span>  
  
5. <span data-ttu-id="aabc3-118">Vyberte typ v proxy straně klienta, ke kterému se má vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="aabc3-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="aabc3-119">Obvykle se jedná o typ vrácený metodou nabízenou webovou službou.</span><span class="sxs-lookup"><span data-stu-id="aabc3-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="aabc3-120">Pole zvoleného typu musí být vystavena jako veřejné vlastnosti pro účely vazby.</span><span class="sxs-lookup"><span data-stu-id="aabc3-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6. <span data-ttu-id="aabc3-121">Nastavte vlastnost <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource> na požadovaný typ, který je obsažený v proxy straně klienta webové služby.</span><span class="sxs-lookup"><span data-stu-id="aabc3-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="aabc3-122">Vytvoření vazby ovládacích prvků k objektu BindingSource, který je svázán s webovou službou</span><span class="sxs-lookup"><span data-stu-id="aabc3-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
- <span data-ttu-id="aabc3-123">Navažte ovládací prvky na <xref:System.Windows.Forms.BindingSource>a předejte veřejnou vlastnost typu webové služby, kterou chcete zadat jako parametr.</span><span class="sxs-lookup"><span data-stu-id="aabc3-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="aabc3-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="aabc3-124">Example</span></span>  
 <span data-ttu-id="aabc3-125">Následující příklad kódu ukazuje, jak vytvořit navázání součásti <xref:System.Windows.Forms.BindingSource> k webové službě a jak navazovat textové pole na <xref:System.Windows.Forms.BindingSource> komponentu.</span><span class="sxs-lookup"><span data-stu-id="aabc3-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="aabc3-126">Po kliknutí na tlačítko se zavolá metoda webové služby a výsledky se zobrazí v `textbox1`.</span><span class="sxs-lookup"><span data-stu-id="aabc3-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aabc3-127">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="aabc3-127">Compiling the Code</span></span>  
 <span data-ttu-id="aabc3-128">Toto je kompletní příklad, který obsahuje metodu `Main` a zkrácenou verzi kódu proxy na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="aabc3-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="aabc3-129">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="aabc3-129">This example requires:</span></span>  
  
- <span data-ttu-id="aabc3-130">Odkazy na sestavení System, System. Drawing, System. Web. Services, System. Windows. Forms a System. XML.</span><span class="sxs-lookup"><span data-stu-id="aabc3-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aabc3-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aabc3-131">See also</span></span>

- [<span data-ttu-id="aabc3-132">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="aabc3-132">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="aabc3-133">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="aabc3-133">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)

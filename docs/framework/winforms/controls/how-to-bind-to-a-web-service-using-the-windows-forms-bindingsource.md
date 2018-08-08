---
title: 'Postupy: Připojení k webové službě pomocí Windows Forms BindingSource'
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
ms.openlocfilehash: 5a5db651b0690aae393666124c8d33402d57a189
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531395"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="a25e5-102">Postupy: Připojení k webové službě pomocí Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="a25e5-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="a25e5-103">Pokud chcete vytvořit vazbu ovládacího prvku formuláře Windows do výsledků získaných z volání webové služby XML, můžete použít <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="a25e5-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="a25e5-104">Tento postup je podobný vazby <xref:System.Windows.Forms.BindingSource> součásti typu.</span><span class="sxs-lookup"><span data-stu-id="a25e5-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="a25e5-105">Je nutné vytvořit proxy server na straně klienta, který obsahuje metody a typy, které jsou vystavené webovou službu.</span><span class="sxs-lookup"><span data-stu-id="a25e5-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="a25e5-106">Vygenerování proxy server na straně klienta z webové služby (.asmx) sám sebe nebo jeho webové služby (soubor Description Language WSDL).</span><span class="sxs-lookup"><span data-stu-id="a25e5-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="a25e5-107">Váš klientský proxy server musí navíc vystavovat pole komplexní typy používané webovou službu jako veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a25e5-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="a25e5-108">Pak vytvořte vazbu <xref:System.Windows.Forms.BindingSource> na jeden z typů, které jsou zveřejněné na webu služby proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="a25e5-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="a25e5-109">Vytvoření a vytvořit vazbu na straně klienta proxy</span><span class="sxs-lookup"><span data-stu-id="a25e5-109">To create and bind to a client-side proxy</span></span>  
  
1.  <span data-ttu-id="a25e5-110">Vytvoření formuláře Windows v adresáři podle vaší volby, s odpovídající obor názvů.</span><span class="sxs-lookup"><span data-stu-id="a25e5-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2.  <span data-ttu-id="a25e5-111">Přidat <xref:System.Windows.Forms.BindingSource> součásti pro formulář.</span><span class="sxs-lookup"><span data-stu-id="a25e5-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3.  <span data-ttu-id="a25e5-112">Otevřete [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] příkazový řádek a přejděte na stejný adresář, který svého formuláře se nachází v.</span><span class="sxs-lookup"><span data-stu-id="a25e5-112">Open the [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4.  <span data-ttu-id="a25e5-113">Pomocí nástroje WSDL zadejte `wsdl` adresu URL pro .asmx nebo soubor WSDL pro webovou službu, za nímž následuje obor názvů aplikace a volitelně jazyk, ve které pracujete.</span><span class="sxs-lookup"><span data-stu-id="a25e5-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="a25e5-114">Následující příklad kódu používá webovou službu v http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx.</span><span class="sxs-lookup"><span data-stu-id="a25e5-114">The following code example uses the Web service located at http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx.</span></span> <span data-ttu-id="a25e5-115">Například pro C# typ `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, nebo pro typ jazyka Visual Basic `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span><span class="sxs-lookup"><span data-stu-id="a25e5-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="a25e5-116">Předání cestu jako argument schématu WSDL nástroj vygeneruje proxy serveru klienta ve stejné adresáře a oboru názvů jako je aplikace, v daném jazyce.</span><span class="sxs-lookup"><span data-stu-id="a25e5-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="a25e5-117">Pokud používáte Visual Studio, přidejte do projektu soubor.</span><span class="sxs-lookup"><span data-stu-id="a25e5-117">If you are using Visual Studio, add the file to your project.</span></span>  
  
5.  <span data-ttu-id="a25e5-118">Vyberte typ proxy serveru klienta pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="a25e5-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="a25e5-119">To je obvykle typ vrácený metodou nabízené webovou službou.</span><span class="sxs-lookup"><span data-stu-id="a25e5-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="a25e5-120">Pole zvoleného typu musí být zveřejněné jako veřejné vlastnosti pro účely vazby.</span><span class="sxs-lookup"><span data-stu-id="a25e5-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  <span data-ttu-id="a25e5-121">Nastavte <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost <xref:System.Windows.Forms.BindingSource> na typ, který chcete obsažené v proxy serveru webové služby klienta.</span><span class="sxs-lookup"><span data-stu-id="a25e5-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="a25e5-122">Vázání ovládacích prvků na BindingSource, který je vázaný k webové službě</span><span class="sxs-lookup"><span data-stu-id="a25e5-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
-   <span data-ttu-id="a25e5-123">Vytvoření vazby ovládacích prvků na <xref:System.Windows.Forms.BindingSource>, předávání veřejná vlastnost typu webové služby, který chcete jako parametr.</span><span class="sxs-lookup"><span data-stu-id="a25e5-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="a25e5-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="a25e5-124">Example</span></span>  
 <span data-ttu-id="a25e5-125">Následující příklad kódu ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.BindingSource> součást webové služby a jak vytvořit vazbu textové pole k <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="a25e5-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="a25e5-126">Když kliknete na tlačítko, je volána metoda webové služby a výsledky se zobrazí v `textbox1`.</span><span class="sxs-lookup"><span data-stu-id="a25e5-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a25e5-127">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a25e5-127">Compiling the Code</span></span>  
 <span data-ttu-id="a25e5-128">Toto je kompletní příklad, který zahrnuje `Main` metoda a zkrácená verze kódu proxy server na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="a25e5-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="a25e5-129">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a25e5-129">This example requires:</span></span>  
  
-   <span data-ttu-id="a25e5-130">Odkazy na systém, System.Drawing, System.Web.Services, System.Windows.Forms a System.Xml sestavení.</span><span class="sxs-lookup"><span data-stu-id="a25e5-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="a25e5-131">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a25e5-131">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a25e5-132">Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="a25e5-132">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="a25e5-133">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="a25e5-133">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25e5-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="a25e5-134">See Also</span></span>  
 [<span data-ttu-id="a25e5-135">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="a25e5-135">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="a25e5-136">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="a25e5-136">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)

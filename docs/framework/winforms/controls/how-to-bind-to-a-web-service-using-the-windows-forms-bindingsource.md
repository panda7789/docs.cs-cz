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
ms.openlocfilehash: 0ea95ad21ee02745e835dc469ec3849af5a5a2d7
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219890"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="a5f2f-102">Postupy: Připojení k webové službě pomocí Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="a5f2f-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="a5f2f-103">Pokud chcete vytvořit vazbu ovládacího prvku Windows Form do výsledků získaných z volání webové služby XML, můžete použít <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="a5f2f-104">Tento postup je podobný vazby <xref:System.Windows.Forms.BindingSource> komponentu do typu.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="a5f2f-105">Je nutné vytvořit proxy server na straně klienta, který obsahuje metody a typy, které jsou vystavené webové služby.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="a5f2f-106">Generování proxy server na straně klienta z webové služby (.asmx) samotný nebo jeho soubor webové služby WSDL (Description Language).</span><span class="sxs-lookup"><span data-stu-id="a5f2f-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="a5f2f-107">Váš proxy server na straně klienta navíc musí vystavit pole komplexní typy použité ve webové službě jako veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="a5f2f-108">Pak vytvoříte vazbu <xref:System.Windows.Forms.BindingSource> na jeden z typů v webové služby serveru proxy.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="a5f2f-109">K vytvoření a připojení k proxy serveru na straně klienta</span><span class="sxs-lookup"><span data-stu-id="a5f2f-109">To create and bind to a client-side proxy</span></span>  
  
1.  <span data-ttu-id="a5f2f-110">Vytvoření formuláře Windows v adresáři podle vašeho výběru s odpovídající obor názvů.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2.  <span data-ttu-id="a5f2f-111">Přidat <xref:System.Windows.Forms.BindingSource> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3.  <span data-ttu-id="a5f2f-112">Otevřít [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] příkazový řádek a přejděte do stejného adresáře, umístěný ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-112">Open the [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4.  <span data-ttu-id="a5f2f-113">Pomocí nástroje WSDL zadat `wsdl` a adresa URL pro .asmx nebo souboru WSDL pro webovou službu, za nímž následuje obor názvů vaší aplikace a volitelně jazyk k práci používáte.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="a5f2f-114">Následující příklad kódu používá webovou službu v `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-114">The following code example uses the Web service located at `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span></span> <span data-ttu-id="a5f2f-115">Například pro typ jazyka C# `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, nebo pro typ jazyka Visual Basic `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="a5f2f-116">Předáním cesty do jazyka WSDL jako argument nástroj vygeneruje proxy server na straně klienta ve stejném adresáři a obor názvů jako vaši aplikaci v daném jazyce.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="a5f2f-117">Pokud používáte Visual Studio, přidejte soubor do projektu.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-117">If you are using Visual Studio, add the file to your project.</span></span>  
  
5.  <span data-ttu-id="a5f2f-118">Vyberte typ proxy serveru na straně klienta k vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="a5f2f-119">Obvykle se jedná o typ vrácený metodou nabízené webové služby.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="a5f2f-120">Pole zvolený typ musí být vystavené jako veřejné vlastnosti pro účely vazby.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  <span data-ttu-id="a5f2f-121">Nastavte <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost <xref:System.Windows.Forms.BindingSource> na požadovaný typ, který je obsažen v proxy serveru webové služby na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="a5f2f-122">K vytvoření vazby ovládacích prvků do objektu BindingSource, který je vázán k webové službě</span><span class="sxs-lookup"><span data-stu-id="a5f2f-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
-   <span data-ttu-id="a5f2f-123">Vytvoření vazby ovládacích prvků <xref:System.Windows.Forms.BindingSource>, veřejná vlastnost typ webové služby, který chcete, aby se předá jako parametr.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="a5f2f-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5f2f-124">Example</span></span>  
 <span data-ttu-id="a5f2f-125">Následující příklad kódu ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.BindingSource> součást webové služby a jak vytvořit vazbu textové pole <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="a5f2f-126">Když kliknete na tlačítko, je volána metoda webové služby a výsledky se zobrazí v `textbox1`.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a5f2f-127">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a5f2f-127">Compiling the Code</span></span>  
 <span data-ttu-id="a5f2f-128">Toto je úplný příklad, který zahrnuje `Main` metoda a zkrácenou verzi kódu proxy server na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="a5f2f-129">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a5f2f-129">This example requires:</span></span>  
  
-   <span data-ttu-id="a5f2f-130">Odkazy na sestavení systému, System.Drawing, System.Web.Services, System.Windows.Forms a System.Xml.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="a5f2f-131">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a5f2f-131">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a5f2f-132">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="a5f2f-132">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f2f-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5f2f-133">See also</span></span>
- [<span data-ttu-id="a5f2f-134">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="a5f2f-134">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [<span data-ttu-id="a5f2f-135">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="a5f2f-135">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)

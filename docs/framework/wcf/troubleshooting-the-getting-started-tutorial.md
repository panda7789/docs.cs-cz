---
title: Odstraňování problémů v kurzu Začínáme
ms.date: 03/30/2017
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 5b8cd04ef4d98e522e255e1b7529e848351b2e0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695657"
---
# <a name="troubleshooting-the-getting-started-tutorial"></a><span data-ttu-id="1fba0-102">Odstraňování problémů v kurzu Začínáme</span><span class="sxs-lookup"><span data-stu-id="1fba0-102">Troubleshooting the Getting Started Tutorial</span></span>
<span data-ttu-id="1fba0-103">Toto téma uvádí nejběžnější problémy vzniklé při práci prostřednictvím kurzu Začínáme a způsob jejich řešení.</span><span class="sxs-lookup"><span data-stu-id="1fba0-103">This topic lists the most common problems encountered when working through the Getting Started Tutorial and how to resolve them.</span></span>  
  
<span data-ttu-id="1fba0-104">**Nejde najít soubory projektu na pevném disku.**</span><span class="sxs-lookup"><span data-stu-id="1fba0-104">**I am unable to find the project files on my hard drive.**</span></span>

 <span data-ttu-id="1fba0-105">Visual Studio uloží soubory projektu v c:\users\\<user name>\Documents\\< verze sady Visual Studio\>\Projects.</span><span class="sxs-lookup"><span data-stu-id="1fba0-105">Visual Studio saves project files in c:\users\\<user name>\Documents\\<Visual Studio version\>\Projects.</span></span>  
  
<span data-ttu-id="1fba0-106">**Došlo k pokusu o spuštění služby aplikace: Protokol HTTP nemohl zaregistrovat adresu URL `http://+:8000/ServiceModelSamples/Service/`.** 
 **Váš proces nemá přístupová práva k tomuto oboru názvů.**</span><span class="sxs-lookup"><span data-stu-id="1fba0-106">**Attempting to run the service application: HTTP could not register URL `http://+:8000/ServiceModelSamples/Service/`.**
**Your process does not have access rights to this namespace.**</span></span> 

 <span data-ttu-id="1fba0-107">Proces, který hostuje službu WCF musí být spuštěn s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="1fba0-107">The process that hosts a WCF service must be run with Administrative privileges.</span></span> <span data-ttu-id="1fba0-108">Pokud používáte službu ze sady Visual Studio, musíte spustit aplikaci Visual Studio jako správce.</span><span class="sxs-lookup"><span data-stu-id="1fba0-108">If you are running the service from inside Visual Studio, you must run Visual Studio as an Administrator.</span></span> <span data-ttu-id="1fba0-109">Klepněte na tlačítko **Start**, klikněte pravým tlačítkem na **sady Visual Studio \< *verze* >**  a vyberte **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="1fba0-109">To do so click **Start**, right-click **Visual Studio \<*version*>** and select **Run As Administrator**.</span></span> <span data-ttu-id="1fba0-110">Pokud používáte službu z příkazového řádku v okně konzoly, musí v okně konzoly spusťte jako správce podobným způsobem.</span><span class="sxs-lookup"><span data-stu-id="1fba0-110">If you are running the service from a command-line prompt in a console window, you must start the console window as an Administrator in a similar way.</span></span> <span data-ttu-id="1fba0-111">Klikněte na tlačítko **Start**, klikněte pravým tlačítkem na **příkazového řádku** a vyberte **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="1fba0-111">Click **Start**, right-click **Command Prompt** and select **Run As Administrator**.</span></span>  
  
<span data-ttu-id="1fba0-112">**Pokus o použití nástroje Svcutil.exe: 'svcutil' nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru.**</span><span class="sxs-lookup"><span data-stu-id="1fba0-112">**Attempting to use the Svcutil.exe tool: 'svcutil' is not recognized as an internal or external command, operable program or batch file.**</span></span>

 <span data-ttu-id="1fba0-113">Svcutil.exe musí být v systémové cestě.</span><span class="sxs-lookup"><span data-stu-id="1fba0-113">Svcutil.exe must be in the system path.</span></span> <span data-ttu-id="1fba0-114">Nejjednodušším řešením je použít příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="1fba0-114">The easiest solution is to use the Command Prompt.</span></span> <span data-ttu-id="1fba0-115">Klikněte na tlačítko **Start**vyberte **všechny programy**, **sady Visual Studio \< *verze*>**,  **Nástroje sady Visual Studio**, a **Developer Command Prompt pro sadu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1fba0-115">Click **Start**, select **All Programs**, **Visual Studio \<*version*>**, **Visual Studio Tools**, and **Developer Command Prompt for Visual Studio**.</span></span> <span data-ttu-id="1fba0-116">Tento příkazový řádek nastaví systémové cesty na správné umístění pro všechny nástroje dodávané jako součást sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1fba0-116">This command prompt sets the system path to the correct locations for all tools shipped as part of Visual Studio.</span></span>  

<span data-ttu-id="1fba0-117">**Nepovedlo se najít soubor App.config generovaných Svcutil.exe.**</span><span class="sxs-lookup"><span data-stu-id="1fba0-117">**Unable to find the App.config file generated by Svcutil.exe.**</span></span>

 <span data-ttu-id="1fba0-118">**Přidat existující položku** dialogové okno zobrazí ve výchozím nastavení pouze soubory s těmito příponami: .cs, .resx, .settings, XSD, WSDL.</span><span class="sxs-lookup"><span data-stu-id="1fba0-118">The **Add Existing Item** dialog only displays files with the following extensions by default: .cs, .resx, .settings, .xsd, .wsdl.</span></span> <span data-ttu-id="1fba0-119">Můžete určit, že chcete zobrazit všechny typy souborů tak, že vyberete **všechny soubory (\*.\*)**  v rozevíracím seznamu v pravém dolním rohu **přidat existující položku** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="1fba0-119">You can specify that you want to see all file types by selecting **All Files (\*.\*)** in the drop-down list box in the lower right corner of the **Add Existing Item** dialog box.</span></span>  


<span data-ttu-id="1fba0-120">**Kompilování klientská aplikace: 'CalculatorClient' neobsahuje definici pro '\<název metody > "a žádná metoda rozšíření '\<název metody >' přijímala první argument typu 'CalculatorClient' nebyla nalezena. (nechybí using – direktiva nebo odkaz na sestavení?)**</span><span class="sxs-lookup"><span data-stu-id="1fba0-120">**Compiling the client application: 'CalculatorClient' does not contain a definition for '\<method name>' and no extension method '\<method name>' accepting a first argument of type 'CalculatorClient' could be found (are you missing a using directive or an assembly reference?)**</span></span>  

<span data-ttu-id="1fba0-121">Pouze těch metod, které jsou označené `ServiceOperationAttribute` jsou vystaveny vnějším světem.</span><span class="sxs-lookup"><span data-stu-id="1fba0-121">Only those methods that are marked with the `ServiceOperationAttribute` are exposed to the outside world.</span></span> <span data-ttu-id="1fba0-122">Pokud je vynechán `ServiceOperationAttribute` atribut z jedné z metod v `ICalculator` rozhraní, dostanete tuto chybovou zprávu při kompilaci klientskou aplikaci, která provádí volání na operaci chybí atribut.</span><span class="sxs-lookup"><span data-stu-id="1fba0-122">If you omitted the `ServiceOperationAttribute` attribute from one of the methods in the `ICalculator` interface, you get this error message when compiling a client application that makes a call to the operation missing the attribute.</span></span>  

<span data-ttu-id="1fba0-123">**Kompilování klientská aplikace: Typ nebo obor názvů 'CalculatorClient' nebyl nalezen. (nechybí using – direktiva nebo odkaz na sestavení?)**</span><span class="sxs-lookup"><span data-stu-id="1fba0-123">**Compiling the client application: The type or namespace name 'CalculatorClient' could not be found (are you missing a using directive or an assembly reference?)**</span></span>

 <span data-ttu-id="1fba0-124">K této chybě získáte, pokud nepřidáte Proxy.cs nebo Proxy.vb soubor do projektu klienta.</span><span class="sxs-lookup"><span data-stu-id="1fba0-124">You get this error if you do not add the Proxy.cs or Proxy.vb file to your client project.</span></span>  

<span data-ttu-id="1fba0-125">**Spuštění klienta: Neošetřená výjimka: System.ServiceModel.EndpointNotFoundException: Nelze se připojit k `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`. Kód chyby TCP 10061: Protože cílový počítač aktivně odmítl může nevytváří žádné připojení.**</span><span class="sxs-lookup"><span data-stu-id="1fba0-125">**Running the client: Unhandled Exception: System.ServiceModel.EndpointNotFoundException: Could not connect to `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`. TCP error code 10061: No connection could be made because the target machine actively refused it.**</span></span>

<span data-ttu-id="1fba0-126">K této chybě dochází, pokud spuštění klientské aplikace bez nutnosti spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="1fba0-126">This error occurs if you run the client application without running the service.</span></span>  
  
<span data-ttu-id="1fba0-127">**Neošetřená výjimka: System.ServiceModel.Security.SecurityNegotiationException: Vyjednávání zabezpečení SOAP s `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` pro cíl `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` se nezdařilo**</span><span class="sxs-lookup"><span data-stu-id="1fba0-127">**Unhandled Exception: System.ServiceModel.Security.SecurityNegotiationException: SOAP security negotiation with `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` for target `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` failed**</span></span>  

<span data-ttu-id="1fba0-128">K této chybě dochází v počítači připojeném k doméně, která nemá připojení k síti.</span><span class="sxs-lookup"><span data-stu-id="1fba0-128">This error occurs on a domain-joined computer that does not have network connectivity.</span></span> <span data-ttu-id="1fba0-129">Připojení počítače k síti nebo vypnout zabezpečení klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="1fba0-129">Either connect your computer to the network or turn off security for both the client and the service.</span></span> <span data-ttu-id="1fba0-130">Pro službu upravte kód, který se vytvoří vazba WSHttpBinding takto.</span><span class="sxs-lookup"><span data-stu-id="1fba0-130">For the service, modify the code that creates the WSHttpBinding to the following.</span></span>  
  
```csharp
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```

<span data-ttu-id="1fba0-131">Pro klienta, změnit  **\<zabezpečení >** element v rámci  **\<vazby >** – element pro následující:</span><span class="sxs-lookup"><span data-stu-id="1fba0-131">For the client, change the **\<security>** element under the **\<binding>** element to the following:</span></span>  
  
```xml
<security mode="Node" />  
```  

## <a name="see-also"></a><span data-ttu-id="1fba0-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1fba0-132">See also</span></span>
- [<span data-ttu-id="1fba0-133">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="1fba0-133">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="1fba0-134">Řešení problémů s WCF – úvodní příručka</span><span class="sxs-lookup"><span data-stu-id="1fba0-134">WCF Troubleshooting Quickstart</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)
- [<span data-ttu-id="1fba0-135">Řešení problémů s instalací</span><span class="sxs-lookup"><span data-stu-id="1fba0-135">Troubleshooting Setup Issues</span></span>](../../../docs/framework/wcf/troubleshooting-setup-issues.md)

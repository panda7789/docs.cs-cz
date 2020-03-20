---
title: Řešení potíží s WCF – úvodní příručka
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: f85d37fde19767d7fd1e3002776b4816666cc7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183046"
---
# <a name="wcf-troubleshooting-quickstart"></a><span data-ttu-id="a4efd-102">Řešení potíží s WCF – úvodní příručka</span><span class="sxs-lookup"><span data-stu-id="a4efd-102">WCF Troubleshooting Quickstart</span></span>
<span data-ttu-id="a4efd-103">Toto téma uvádí řadu známých problémů, které zákazníci narazili při vývoji klientů wcf a služeb.</span><span class="sxs-lookup"><span data-stu-id="a4efd-103">This topic lists a number of known issues customers have run into while developing WCF clients and services.</span></span> <span data-ttu-id="a4efd-104">Pokud problém, do který pracujete, není v tomto seznamu, doporučujeme nakonfigurovat trasování pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="a4efd-104">If the issue you are running into is not in this list, we recommend you configure tracing for your service.</span></span> <span data-ttu-id="a4efd-105">Tím se vygeneruje trasovací soubor, který můžete zobrazit pomocí prohlížeče trasovacích souborů, a získáte podrobné informace o výjimkách, ke kterým může v rámci služby dostat.</span><span class="sxs-lookup"><span data-stu-id="a4efd-105">This will generate a trace file that you can view with the trace file viewer and get detailed information about exceptions that may be occurring within the service.</span></span> <span data-ttu-id="a4efd-106">Další informace o konfiguraci trasování naleznete v [tématu: Konfigurace trasování](./diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="a4efd-106">For more information on configuring tracing, see: [Configuring Tracing](./diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="a4efd-107">Další informace o prohlížeči trasovacích souborů naleznete v [tématu: Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a4efd-107">For more information on the trace file viewer, see: [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
1. [<span data-ttu-id="a4efd-108">Po instalaci systému Windows 7 a služby IIS se při pokusu o přechod na službu WCF zobrazí následující chybová zpráva: Chyba PROTOKOLU HTTP 404.3 – nebyl nalezen</span><span class="sxs-lookup"><span data-stu-id="a4efd-108">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>](#bkmk_0)  
  
     <span data-ttu-id="a4efd-109">Chyba protokolu HTTP 404.3 – nebyla nalezenaStránka, kterou požadujete, nemůže být obsluhována z důvodu konfigurace rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a4efd-109">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="a4efd-110">Pokud je stránka skript, přidejte obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="a4efd-110">If the page is a script, add a handler.</span></span> <span data-ttu-id="a4efd-111">Pokud by měl být soubor stažen, přidejte mapu MIME.</span><span class="sxs-lookup"><span data-stu-id="a4efd-111">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="a4efd-112">Podrobné informace o chyběModul StaticFileModule.</span><span class="sxs-lookup"><span data-stu-id="a4efd-112">Detailed Error InformationModule StaticFileModule.</span></span>  
  
2. [<span data-ttu-id="a4efd-113">Někdy obdržím MessageSecurityException na druhý požadavek, pokud můj klient je nečinný na chvíli po první požadavek. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-113">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request. What is happening?</span></span>](#BKMK_q1)  
  
3. [<span data-ttu-id="a4efd-114">Moje služba začne odmítat nové klienty poté, co s ní spolupracuje asi 10 klientů. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-114">My service starts to reject new clients after about 10 clients are interacting with it. What is happening?</span></span>](#BKMK_q2)  
  
4. [<span data-ttu-id="a4efd-115">Je možné načíst konfiguraci služby z jiného místa než z konfiguračního souboru aplikace WCF?</span><span class="sxs-lookup"><span data-stu-id="a4efd-115">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>](#BKMK_q3)  
  
5. [<span data-ttu-id="a4efd-116">Moje služba a klient fungují skvěle, ale nemohu je dostat do práce, když je klient na jiném počítači? Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-116">My service and client work great, but I can’t get them to work when the client is on another computer? What’s happening?</span></span>](#BKMK_q4)  
  
6. [<span data-ttu-id="a4efd-117">Při vyvolání FaultException\<Exception>, kde typ je výjimka, vždy obdrží obecný FaultException typ na straně klienta a nikoli obecný typ. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-117">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type. What’s happening?</span></span>](#BKMK_q5)  
  
7. [<span data-ttu-id="a4efd-118">Zdá se, že jednosměrné operace a operace požadavku a odpovědi se vrátí přibližně stejnou rychlostí, když odpověď neobsahuje žádná data. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-118">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data. What's happening?</span></span>](#BKMK_q6)  
  
8. [<span data-ttu-id="a4efd-119">Používám certifikát X.509 se svou službou a dostanu System.Security.Cryptography.CryptographicException. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-119">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException. What’s happening?</span></span>](#BKMK_q77)  
  
9. [<span data-ttu-id="a4efd-120">Změnil jsem první parametr operace z velkých na malá písmena; Teď můj klient vyvolá výjimku. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-120">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception. What's happening?</span></span>](#BKMK_q88)  
  
10. [<span data-ttu-id="a4efd-121">Používám jeden z mých nástrojů trasování a získají EndpointNotFoundException. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-121">I’m using one of my tracing tools and I get an EndpointNotFoundException. What’s happening?</span></span>](#BKMK_q99)  
  
11. [<span data-ttu-id="a4efd-122">Při volání webové http aplikace WCF z aplikace WCF SOAP vrátí služba následující chybu: Metoda 405 není povolena.</span><span class="sxs-lookup"><span data-stu-id="a4efd-122">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>](#BK_MK99)  
  
 [<span data-ttu-id="a4efd-123">Jaká je základní adresa? Jak souvisí s adresou koncového bodu?</span><span class="sxs-lookup"><span data-stu-id="a4efd-123">What is the base address? How does it relate to an endpoint address?</span></span>](#BKMK_q10)  
  
<a name="bkmk_0"></a>
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a><span data-ttu-id="a4efd-124">Po instalaci systému Windows 7 a služby IIS se při pokusu o přechod na službu WCF zobrazí následující chybová zpráva: Chyba PROTOKOLU HTTP 404.3 – nebyl nalezen</span><span class="sxs-lookup"><span data-stu-id="a4efd-124">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>  
 <span data-ttu-id="a4efd-125">Úplná chybová zpráva je:</span><span class="sxs-lookup"><span data-stu-id="a4efd-125">The full error message is:</span></span>  
  
 <span data-ttu-id="a4efd-126">Chyba protokolu HTTP 404.3 – nebyla nalezenaStránka, kterou požadujete, nemůže být obsluhována z důvodu konfigurace rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a4efd-126">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="a4efd-127">Pokud je stránka skript, přidejte obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="a4efd-127">If the page is a script, add a handler.</span></span> <span data-ttu-id="a4efd-128">Pokud by měl být soubor stažen, přidejte mapu MIME.</span><span class="sxs-lookup"><span data-stu-id="a4efd-128">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="a4efd-129">Podrobné informace o chyběModul StaticFileModule.</span><span class="sxs-lookup"><span data-stu-id="a4efd-129">Detailed Error InformationModule StaticFileModule.</span></span>  
  
 <span data-ttu-id="a4efd-130">Tato chybová zpráva se zobrazí, pokud není v ovládacím panelu explicitně nastavena aktivace http služby Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="a4efd-130">This error message occurs when "Windows Communication Foundation HTTP Activation" is not explicitly set in the Control Panel.</span></span> <span data-ttu-id="a4efd-131">Chcete-li tuto možnost nastavit, přejděte do Ovládacích panelů, klepněte na položku Programy v levém dolním rohu okna.</span><span class="sxs-lookup"><span data-stu-id="a4efd-131">To set this go to the Control Panel, click Programs in the lower left-hand corner of the window.</span></span> <span data-ttu-id="a4efd-132">Klikněte na Zapnout nebo vypnout funkce Windows.</span><span class="sxs-lookup"><span data-stu-id="a4efd-132">Click Turn Windows features on or off.</span></span> <span data-ttu-id="a4efd-133">Rozbalte rozhraní Microsoft .NET Framework 3.5.1 a vyberte aktivaci protokolu HTTP nadace Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="a4efd-133">Expand Microsoft .NET Framework 3.5.1 and select Windows Communication Foundation HTTP Activation.</span></span>  
  
<a name="BKMK_q1"></a>
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a><span data-ttu-id="a4efd-134">Někdy obdržím MessageSecurityException na druhý požadavek, pokud můj klient je nečinný na chvíli po první požadavek.</span><span class="sxs-lookup"><span data-stu-id="a4efd-134">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request.</span></span> <span data-ttu-id="a4efd-135">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-135">What is happening?</span></span>  
 <span data-ttu-id="a4efd-136">Druhý požadavek může selhat především ze dvou důvodů: (1) relace časový mat nebo (2) webový server, který je hostitelem služby je recyklován.</span><span class="sxs-lookup"><span data-stu-id="a4efd-136">The second request can fail primarily for two reasons: (1) the session has timed out or (2) the Web server that is hosting the service is recycled.</span></span> <span data-ttu-id="a4efd-137">V prvním případě je relace platná, dokud nevyjde časový čas služby. Pokud služba neobdrží požadavek od klienta ve lhůtě určené ve<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>vazbě služby ( ), služba ukončí relaci zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a4efd-137">In the first case, the session is valid until the service times out. When the service does not receive a request from the client within the period of time specified in the service's binding (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), the service terminates the security session.</span></span> <span data-ttu-id="a4efd-138">Následné klientské zprávy <xref:System.ServiceModel.Security.MessageSecurityException>za následek .</span><span class="sxs-lookup"><span data-stu-id="a4efd-138">Subsequent client messages result in the <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="a4efd-139">Klient musí znovu vytvořit zabezpečené relace se službou k odesílání budoucích zpráv nebo použít stavový token kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a4efd-139">The client must re-establish a secure session with the service to send future messages or use a stateful security context token.</span></span> <span data-ttu-id="a4efd-140">Stavové kontextové tokeny zabezpečení také umožňují zabezpečené relaci přežít recyklovaný webový server.</span><span class="sxs-lookup"><span data-stu-id="a4efd-140">Stateful security context tokens also allow a secure session to survive a Web server being recycled.</span></span> <span data-ttu-id="a4efd-141">Další informace o použití stavových tokenů zabezpečeného kontextu v zabezpečené relaci naleznete v tématu [How to: Create a Security Context Token for a Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="a4efd-141">For more information about using stateful secure context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span> <span data-ttu-id="a4efd-142">Můžete také zakázat zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="a4efd-142">Alternatively, you can disable secure sessions.</span></span> <span data-ttu-id="a4efd-143">Při použití [ \<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) vazba, `establishSecurityContext` můžete `false` nastavit vlastnost zakázat zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="a4efd-143">When you use the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) binding, you can set the `establishSecurityContext` property to `false` to disable secure sessions.</span></span> <span data-ttu-id="a4efd-144">Chcete-li zakázat zabezpečené relace pro jiné vazby, musíte vytvořit vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="a4efd-144">To disable secure sessions for other bindings, you must create a custom binding.</span></span> <span data-ttu-id="a4efd-145">Podrobnosti o vytvoření vlastní vazby naleznete v [tématu Postup: Vytvoření vlastní vazby pomocí SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="a4efd-145">For details about creating a custom binding, see [How to: Create a Custom Binding Using the SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="a4efd-146">Před použitím některé z těchto možností je nutné pochopit požadavky na zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4efd-146">Before you apply any of these options, you must understand your application's security requirements.</span></span>  
  
<a name="BKMK_q2"></a>
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a><span data-ttu-id="a4efd-147">Moje služba začne odmítat nové klienty poté, co s ní spolupracuje asi 10 klientů.</span><span class="sxs-lookup"><span data-stu-id="a4efd-147">My service starts to reject new clients after about 10 clients are interacting with it.</span></span> <span data-ttu-id="a4efd-148">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-148">What is happening?</span></span>  
 <span data-ttu-id="a4efd-149">Ve výchozím nastavení mohou mít služby pouze 10 souběžných relací.</span><span class="sxs-lookup"><span data-stu-id="a4efd-149">By default, services can have only 10 concurrent sessions.</span></span> <span data-ttu-id="a4efd-150">Proto pokud vazby služby používají relace, služba přijímá nová připojení klientů, dokud nedosáhne tohoto čísla, po kterém odmítne nová připojení klienta, dokud jedna z aktuálních relací neskončí.</span><span class="sxs-lookup"><span data-stu-id="a4efd-150">Therefore, if the service bindings use sessions, the service accepts new client connections until it reaches that number, after which it refuses new client connections until one of the current sessions ends.</span></span> <span data-ttu-id="a4efd-151">Můžete podporovat více klientů v mnoha způsoby.</span><span class="sxs-lookup"><span data-stu-id="a4efd-151">You can support more clients in a number of ways.</span></span> <span data-ttu-id="a4efd-152">Pokud vaše služba nevyžaduje relace, nepoužívejte sessionful vazbu.</span><span class="sxs-lookup"><span data-stu-id="a4efd-152">If your service does not require sessions, do not use a sessionful binding.</span></span> <span data-ttu-id="a4efd-153">(Další informace naleznete v tématu [Použití relací](using-sessions.md).) Další možností je zvýšit limit relace změnou <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> hodnoty vlastnosti na číslo odpovídající vaší situaci.</span><span class="sxs-lookup"><span data-stu-id="a4efd-153">(For more information, see [Using Sessions](using-sessions.md).) Another option is to increase the session limit by changing the value of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> property to the number appropriate to your circumstance.</span></span>  
  
<a name="BKMK_q3"></a>
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a><span data-ttu-id="a4efd-154">Je možné načíst konfiguraci služby z jiného místa než z konfiguračního souboru aplikace WCF?</span><span class="sxs-lookup"><span data-stu-id="a4efd-154">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>  
 <span data-ttu-id="a4efd-155">Ano, ale musíte vytvořit vlastní <xref:System.ServiceModel.ServiceHost> třídu, <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> která přepíše metodu.</span><span class="sxs-lookup"><span data-stu-id="a4efd-155">Yes, however, you have to create a custom <xref:System.ServiceModel.ServiceHost> class that overrides the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method.</span></span> <span data-ttu-id="a4efd-156">Uvnitř této metody můžete nejprve zavolat základnu pro načtení konfigurace (pokud chcete také načíst standardní informace o konfiguraci), ale můžete také zcela nahradit systém načítání konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a4efd-156">Inside that method, you can call the base to load configuration first (if you want to load the standard configuration information as well) but you can also entirely replace the configuration loading system.</span></span> <span data-ttu-id="a4efd-157">Pokud chcete načíst konfiguraci z konfiguračního souboru, který se liší od konfiguračního souboru aplikace, musíte analyzovat konfigurační soubor sami a načíst konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a4efd-157">If you want to load configuration from a configuration file that is different from the application configuration file, you must parse the configuration file yourself and load the configuration.</span></span>  
  
 <span data-ttu-id="a4efd-158">Následující příklad kódu ukazuje, jak <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> přepsat metodu a přímo nakonfigurovat koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a4efd-158">The following code example shows how to override the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method and directly configure an endpoint.</span></span>  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a><span data-ttu-id="a4efd-159">Moje služba a klient fungují skvěle, ale nemohu je dostat do práce, když je klient na jiném počítači?</span><span class="sxs-lookup"><span data-stu-id="a4efd-159">My service and client work great, but I can’t get them to work when the client is on another computer?</span></span> <span data-ttu-id="a4efd-160">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-160">What’s happening?</span></span>  
 <span data-ttu-id="a4efd-161">V závislosti na výjimce může existovat několik problémů:</span><span class="sxs-lookup"><span data-stu-id="a4efd-161">Depending upon the exception, there may be several issues:</span></span>  
  
- <span data-ttu-id="a4efd-162">Možná budete muset změnit adresy koncového bodu klienta na název hostitele a ne "localhost".</span><span class="sxs-lookup"><span data-stu-id="a4efd-162">You might need to change the client endpoint addresses to the host name and not "localhost".</span></span>  
  
- <span data-ttu-id="a4efd-163">Je možné, že bude nutné otevřít port aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4efd-163">You might need to open the port to the application.</span></span> <span data-ttu-id="a4efd-164">Podrobnosti naleznete v tématu [Pokyny brány firewall](./samples/firewall-instructions.md) z ukázky sady SDK.</span><span class="sxs-lookup"><span data-stu-id="a4efd-164">For details, see [Firewall Instructions](./samples/firewall-instructions.md) from the SDK samples.</span></span>  
  
- <span data-ttu-id="a4efd-165">Další možné problémy naleznete v tématu ukázky [spuštění ukázky Windows Communication Foundation](./samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4efd-165">For other possible issues, see the samples topic [Running the Windows Communication Foundation Samples](./samples/running-the-samples.md).</span></span>  
  
- <span data-ttu-id="a4efd-166">Pokud váš klient používá pověření systému <xref:System.ServiceModel.Security.SecurityNegotiationException>Windows a výjimkou je , nakonfigurujte protokol Kerberos následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="a4efd-166">If your client is using Windows credentials and the exception is a <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure Kerberos as follows.</span></span>  
  
    1. <span data-ttu-id="a4efd-167">Přidejte pověření identity do prvku koncového bodu v souboru App.config klienta:</span><span class="sxs-lookup"><span data-stu-id="a4efd-167">Add the identity credentials to the endpoint element in the client’s App.config file:</span></span>  
  
        ```xml
        <endpoint
          address="http://MyServer:8000/MyService/"
          binding="wsHttpBinding"
          bindingConfiguration="WSHttpBinding_IServiceExample"
          contract="IServiceExample"
          behaviorConfiguration="ClientCredBehavior"
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2. <span data-ttu-id="a4efd-168">Spusťte samoobslužnou službu pod účtem System nebo NetworkService.</span><span class="sxs-lookup"><span data-stu-id="a4efd-168">Run the self-hosted service under the System or NetworkService account.</span></span> <span data-ttu-id="a4efd-169">Tento příkaz můžete spustit a vytvořit příkazové okno pod systémovým účtem:</span><span class="sxs-lookup"><span data-stu-id="a4efd-169">You can run this command to create a command window under the System account:</span></span>  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. <span data-ttu-id="a4efd-170">Hostuj službu v rámci Internetové informační služby (IIS), která ve výchozím nastavení používá hlavní název služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="a4efd-170">Host the service under Internet Information Services (IIS), which, by default, uses the service principal name (SPN) account.</span></span>  
  
    4. <span data-ttu-id="a4efd-171">Zaregistrujte nový hlavní název služby s doménou pomocí sady SetSPN.</span><span class="sxs-lookup"><span data-stu-id="a4efd-171">Register a new SPN with the domain using SetSPN.</span></span> <span data-ttu-id="a4efd-172">Chcete-li to provést, musíte být správcem domény.</span><span class="sxs-lookup"><span data-stu-id="a4efd-172">You need to be a domain administrator in order to do this.</span></span>  
  
 <span data-ttu-id="a4efd-173">Další informace o protokolu Kerberos naleznete [v tématu Koncepty zabezpečení používané v wcf](./feature-details/security-concepts-used-in-wcf.md) a:</span><span class="sxs-lookup"><span data-stu-id="a4efd-173">For more information about the Kerberos protocol, see [Security Concepts Used in WCF](./feature-details/security-concepts-used-in-wcf.md) and:</span></span>  
  
- [<span data-ttu-id="a4efd-174">Ladění chyb u ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="a4efd-174">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)  
  
- <span data-ttu-id="a4efd-175">[Registrace hlavních názvů služeb protokolu Kerberos pomocí souboru Http.sys](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="a4efd-175">[Registering Kerberos Service Principal Names by Using Http.sys](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))</span></span>  
  
- <span data-ttu-id="a4efd-176">[Kerberos vysvětlil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))</span><span class="sxs-lookup"><span data-stu-id="a4efd-176">[Kerberos Explained](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))</span></span>  
  
<a name="BKMK_q5"></a>
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a><span data-ttu-id="a4efd-177">Při vyvolání FaultException\<Exception>, kde typ je výjimka, vždy obdrží obecný FaultException typ na straně klienta a nikoli obecný typ.</span><span class="sxs-lookup"><span data-stu-id="a4efd-177">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type.</span></span> <span data-ttu-id="a4efd-178">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-178">What’s happening?</span></span>  
 <span data-ttu-id="a4efd-179">Důrazně doporučujeme vytvořit vlastní datový typ vlastní chyby a deklarovat, že jako typ podrobností ve smlouvě o chybě.</span><span class="sxs-lookup"><span data-stu-id="a4efd-179">It is highly recommended that you create your own custom error data type and declare that as the detail type in your fault contract.</span></span> <span data-ttu-id="a4efd-180">Důvodem je, že pomocí systémem poskytované typy výjimek:</span><span class="sxs-lookup"><span data-stu-id="a4efd-180">The reason is that using system-provided exception types:</span></span>  
  
- <span data-ttu-id="a4efd-181">Vytvoří typ závislost, která odebere jednu z největších silných stránek aplikací orientovaných na služby.</span><span class="sxs-lookup"><span data-stu-id="a4efd-181">Creates a type dependency that removes one of the biggest strengths of service-oriented applications.</span></span>  
  
- <span data-ttu-id="a4efd-182">Nelze záviset na výjimkách serializace standardním způsobem.</span><span class="sxs-lookup"><span data-stu-id="a4efd-182">Cannot depend upon exceptions serializing in a standard way.</span></span> <span data-ttu-id="a4efd-183">Některé – <xref:System.Security.SecurityException>jako – nemusí být vůbec serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="a4efd-183">Some—like <xref:System.Security.SecurityException>—may not be serializable at all.</span></span>  
  
- <span data-ttu-id="a4efd-184">Zpřístupní klientům podrobnosti interní implementace.</span><span class="sxs-lookup"><span data-stu-id="a4efd-184">Exposes internal implementation details to clients.</span></span> <span data-ttu-id="a4efd-185">Další informace naleznete [v tématu Určení a zpracování chyb ve smlouvách a službách](specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="a4efd-185">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
 <span data-ttu-id="a4efd-186">Pokud však ladíte aplikaci, můžete serializovat informace o výjimce a <xref:System.ServiceModel.Description.ServiceDebugBehavior> vrátit je klientovi pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="a4efd-186">If you are debugging an application, however, you can serialize exception information and return it to the client by using the <xref:System.ServiceModel.Description.ServiceDebugBehavior> class.</span></span>  
  
<a name="BKMK_q6"></a>
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a><span data-ttu-id="a4efd-187">Zdá se, že jednosměrné operace a operace požadavku a odpovědi se vrátí přibližně stejnou rychlostí, když odpověď neobsahuje žádná data.</span><span class="sxs-lookup"><span data-stu-id="a4efd-187">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data.</span></span> <span data-ttu-id="a4efd-188">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-188">What's happening?</span></span>  
 <span data-ttu-id="a4efd-189">Určení, že operace je jedním ze způsobů, znamená pouze to, že kontrakt operace přijme vstupní zprávu a nevrátí výstupní zprávu.</span><span class="sxs-lookup"><span data-stu-id="a4efd-189">Specifying that an operation is one way means only that the operation contract accepts an input message and does not return an output message.</span></span> <span data-ttu-id="a4efd-190">V WCF všechna vyvolání klienta vrátit při odchozí data byla zapsána do drátu nebo je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="a4efd-190">In WCF, all client invocations return when the outbound data has been written to the wire or an exception is thrown.</span></span> <span data-ttu-id="a4efd-191">Jednosměrné operace fungují stejným způsobem a mohou vyvolat, pokud službu nelze nalézt nebo blokovat, pokud služba není připravena přijmout data ze sítě.</span><span class="sxs-lookup"><span data-stu-id="a4efd-191">One-way operations work the same way, and they can throw if the service cannot be located or block if the service is not prepared to accept the data from the network.</span></span> <span data-ttu-id="a4efd-192">Obvykle v WCF, to má za následek jednosměrné volání návratu klientovi rychleji než požadavek odpověď; ale všechny podmínky, které zpomaluje odesílání odchozích dat v síti zpomaluje jednosměrné operace, jakož i operace požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a4efd-192">Typically in WCF, this results in one-way calls returning to the client more quickly than request-reply; but any condition that slows the sending of the outbound data over the network slows one-way operations as well as request-reply operations.</span></span> <span data-ttu-id="a4efd-193">Další informace naleznete [v tématu Jednosměrné služby](./feature-details/one-way-services.md) a [přístup ke službám pomocí wcf klienta](./feature-details/accessing-services-using-a-client.md).</span><span class="sxs-lookup"><span data-stu-id="a4efd-193">For more information, see [One-Way Services](./feature-details/one-way-services.md) and [Accessing Services Using a WCF Client](./feature-details/accessing-services-using-a-client.md).</span></span>  
  
<a name="BKMK_q77"></a>
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a><span data-ttu-id="a4efd-194">Používám certifikát X.509 se svou službou a dostanu System.Security.Cryptography.CryptographicException.</span><span class="sxs-lookup"><span data-stu-id="a4efd-194">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException.</span></span> <span data-ttu-id="a4efd-195">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-195">What’s happening?</span></span>  
 <span data-ttu-id="a4efd-196">K tomu obvykle dochází po změně uživatelského účtu, pod kterým je spuštěn pracovní proces iis.</span><span class="sxs-lookup"><span data-stu-id="a4efd-196">This commonly occurs after changing the user account under which the IIS worker process runs.</span></span> <span data-ttu-id="a4efd-197">Pokud například v systému Windows XP změníte výchozí uživatelský účet, pod kterým je Aspnet_wp.exe spuštěn z prostředí ASPNET na vlastní uživatelský účet, může se zobrazit tato chyba.</span><span class="sxs-lookup"><span data-stu-id="a4efd-197">For example, in Windows XP, if you change the default user account that the Aspnet_wp.exe runs under from ASPNET to a custom user account, you may see this error.</span></span> <span data-ttu-id="a4efd-198">Pokud používáte soukromý klíč, proces, který jej používá, bude muset mít oprávnění pro přístup k souboru, který tento klíč ukládá.</span><span class="sxs-lookup"><span data-stu-id="a4efd-198">If using a private key, the process that uses it will need to have permissions to access the file storing that key.</span></span>  
  
 <span data-ttu-id="a4efd-199">V takovém případě je nutné udělit oprávnění pro přístup ke čtení k účtu procesu pro soubor obsahující soukromý klíč.</span><span class="sxs-lookup"><span data-stu-id="a4efd-199">If this is the case, you must give read access privileges to the process's account for the file containing the private key.</span></span> <span data-ttu-id="a4efd-200">Pokud je například pracovní proces služby IIS spuštěn pod účtem Bob, budete muset udělit Petrovi přístup pro čtení k souboru obsahujícímu soukromý klíč.</span><span class="sxs-lookup"><span data-stu-id="a4efd-200">For example, if the IIS worker process is running under the Bob account, then you will need to give Bob read access to the file containing the private key.</span></span>  
  
 <span data-ttu-id="a4efd-201">Další informace o tom, jak udělit správný uživatelský účet přístup k souboru, který obsahuje soukromý klíč pro konkrétní certifikát X.509, naleznete v [tématu How to: Make X.509 Certificates Accessible to WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="a4efd-201">For more information about how to give the correct user account access to the file that contains the private key for a specific X.509 certificate, see [How to: Make X.509 Certificates Accessible to WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span></span>  
  
<a name="BKMK_q88"></a>
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a><span data-ttu-id="a4efd-202">Změnil jsem první parametr operace z velkých na malá písmena; Teď můj klient vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="a4efd-202">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception.</span></span> <span data-ttu-id="a4efd-203">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-203">What's happening?</span></span>  
 <span data-ttu-id="a4efd-204">Hodnoty názvů parametrů v podpisu operace jsou součástí smlouvy a rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="a4efd-204">The values of the parameter names in the operation signature are part of the contract and are case-sensitive.</span></span> <span data-ttu-id="a4efd-205">Atribut <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> použijte, pokud potřebujete rozlišovat mezi názvem místního parametru a metadaty, která popisují operaci pro klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4efd-205">Use the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> attribute when you need to distinguish between the local parameter name and the metadata that describes the operation for client applications.</span></span>  
  
<a name="BKMK_q99"></a>
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a><span data-ttu-id="a4efd-206">Používám jeden z mých nástrojů trasování a získají EndpointNotFoundException.</span><span class="sxs-lookup"><span data-stu-id="a4efd-206">I’m using one of my tracing tools and I get an EndpointNotFoundException.</span></span> <span data-ttu-id="a4efd-207">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="a4efd-207">What’s happening?</span></span>  
 <span data-ttu-id="a4efd-208">Pokud používáte nástroj trasování, který není systémem poskytované WCF trasování <xref:System.ServiceModel.EndpointNotFoundException> mechanismus a obdržíte, který označuje, že došlo <xref:System.ServiceModel.Description.ClientViaBehavior> k neshodě filtru adresy, je třeba použít třídu k přesměrování zprávy na nástroj pro trasování a nástroj přesměrovat tyto zprávy na adresu služby.</span><span class="sxs-lookup"><span data-stu-id="a4efd-208">If you are using a tracing tool that is not the system-provided WCF tracing mechanism and you receive an <xref:System.ServiceModel.EndpointNotFoundException> that indicates that there was an address filter mismatch, you need to use the <xref:System.ServiceModel.Description.ClientViaBehavior> class to direct the messages to the tracing utility and have the utility redirect those messages to the service address.</span></span> <span data-ttu-id="a4efd-209">Třída <xref:System.ServiceModel.Description.ClientViaBehavior> změní `Via` adresování záhlaví určit další síťovou adresu odděleně od konečného `To` příjemce, označené adresování záhlaví.</span><span class="sxs-lookup"><span data-stu-id="a4efd-209">The <xref:System.ServiceModel.Description.ClientViaBehavior> class alters the `Via` addressing header to specify the next network address separately from the ultimate receiver, indicated by the `To` addressing header.</span></span> <span data-ttu-id="a4efd-210">Při této této, ale neměňte adresu koncového bodu, který se používá k vytvoření `To` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a4efd-210">When doing this, however, do not change the endpoint address, which is used to establish the `To` value.</span></span>  
  
 <span data-ttu-id="a4efd-211">Následující příklad kódu ukazuje ukázkový konfigurační soubor klienta.</span><span class="sxs-lookup"><span data-stu-id="a4efd-211">The following code example shows an example client configuration file.</span></span>  
  
```xml
<endpoint
  address="http://localhost:8000/MyServer/"  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"
  contract="IMyContract"
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a><span data-ttu-id="a4efd-212">Jaká je základní adresa?</span><span class="sxs-lookup"><span data-stu-id="a4efd-212">What is the base address?</span></span> <span data-ttu-id="a4efd-213">Jak souvisí s adresou koncového bodu?</span><span class="sxs-lookup"><span data-stu-id="a4efd-213">How does it relate to an endpoint address?</span></span>  
 <span data-ttu-id="a4efd-214">Základní adresa je kořenová <xref:System.ServiceModel.ServiceHost> adresa třídy.</span><span class="sxs-lookup"><span data-stu-id="a4efd-214">A base address is the root address for a <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="a4efd-215">Ve výchozím nastavení, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> pokud přidáte třídu do konfigurace služby, jazyk popisu webových služeb (WSDL) pro všechny koncové body, které hostitel publikuje, se načte ze základní adresy HTTP plus jakákoli relativní adresa poskytnutá chování metadat plus "?wsdl".</span><span class="sxs-lookup"><span data-stu-id="a4efd-215">By default, if you add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class into your service configuration, the Web Services Description Language (WSDL) for all endpoints the host publishes are retrieved from the HTTP base address, plus any relative address provided to the metadata behavior, plus "?wsdl".</span></span> <span data-ttu-id="a4efd-216">Pokud jste obeznámeni s ASP.NET a službou IIS, základní adresa je ekvivalentní virtuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="a4efd-216">If you are familiar with ASP.NET and IIS, the base address is equivalent to the virtual directory.</span></span>  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a><span data-ttu-id="a4efd-217">Sdílení portu mezi koncovým bodem služby a koncovým bodem mex pomocí nettcpbinding</span><span class="sxs-lookup"><span data-stu-id="a4efd-217">Sharing a port between a service endpoint and a mex endpoint using the NetTcpBinding</span></span>  
 <span data-ttu-id="a4efd-218">Pokud zadáte základní adresu služby jako net.tcp://MyServer:8080/MyService a přidáte následující koncové body:</span><span class="sxs-lookup"><span data-stu-id="a4efd-218">If you specify the base address for a service as net.tcp://MyServer:8080/MyService and add the following endpoints:</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="a4efd-219">A pokud změníte jedno z nastavení NetTcpBinding, jak je znázorněno v následujícím fragmentu konfigurace:</span><span class="sxs-lookup"><span data-stu-id="a4efd-219">And if you modify one of the NetTcpBinding settings as shown in the following configuration snippet:</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="a4efd-220">Zobrazí se chyba jako následující: Neošetřená výjimka: System.ServiceModel.AddressAlreadyInUseException: V koncovém bodě IP 0.0.0.0:9000 můžete tuto chybu obejít zadáním plně kvalifikované adresy URL s jiným portem pro koncového bodu MEX, jak je znázorněno v následujícím fragmentu konfigurace:</span><span class="sxs-lookup"><span data-stu-id="a4efd-220">You will see an error like the following: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000 You can work around this error by specifying a fully qualified URL with a different port for the MEX endpoint as shown in the following configuration snippet:</span></span>  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a><span data-ttu-id="a4efd-221">Při volání webové http aplikace WCF z aplikace WCF SOAP vrátí služba následující chybu: Metoda 405 není povolena.</span><span class="sxs-lookup"><span data-stu-id="a4efd-221">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>  
 <span data-ttu-id="a4efd-222">Volání aplikace <xref:System.ServiceModel.WebHttpBinding> WCF Web HTTP (služba, <xref:System.ServiceModel.Description.WebHttpBehavior>která používá a ) ze služby WCF může generovat následující výjimku: ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` K této výjimce dochází, protože WCF přepíše odchozí <xref:System.ServiceModel.OperationContext> s příchozí <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="a4efd-222">Calling a WCF Web HTTP application (a service that uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior>) from a WCF service may generate the following exception: ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` This exception occurs because WCF overwrites the outgoing <xref:System.ServiceModel.OperationContext> with the incoming <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="a4efd-223">Chcete-li tento problém <xref:System.ServiceModel.OperationContextScope> vyřešit, vytvořte operaci služby WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="a4efd-223">To solve this problem, create an <xref:System.ServiceModel.OperationContextScope> within the WCF Web HTTP service operation.</span></span> <span data-ttu-id="a4efd-224">Například:</span><span class="sxs-lookup"><span data-stu-id="a4efd-224">For example:</span></span>  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4efd-225">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4efd-225">See also</span></span>

- [<span data-ttu-id="a4efd-226">Ladění chyb u ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="a4efd-226">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)

---
title: "Řešení potíží s WCF – úvodní příručka"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d72afb0fa1c316b981a15ef1e124f21b5be0b09d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-troubleshooting-quickstart"></a><span data-ttu-id="39d68-102">Řešení potíží s WCF – úvodní příručka</span><span class="sxs-lookup"><span data-stu-id="39d68-102">WCF Troubleshooting Quickstart</span></span>
<span data-ttu-id="39d68-103">Toto téma uvádí počet známé problémy, se kterými se zákazníci spustili do při vývoj klienti WCF a služeb.</span><span class="sxs-lookup"><span data-stu-id="39d68-103">This topic lists a number of known issues customers have run into while developing WCF clients and services.</span></span> <span data-ttu-id="39d68-104">Pokud problém, který běží na není v tomto seznamu, doporučujeme že konfigurovat trasování pro služby.</span><span class="sxs-lookup"><span data-stu-id="39d68-104">If the issue you are running into is not in this list, we recommend you configure tracing for your service.</span></span> <span data-ttu-id="39d68-105">Tím se vygeneruje soubor trasování, můžete zobrazit pomocí prohlížeče soubor trasování a získat podrobné informace o výjimkách, který může vyskytovat v rámci služby.</span><span class="sxs-lookup"><span data-stu-id="39d68-105">This will generate a trace file that you can view with the trace file viewer and get detailed information about exceptions that may be occurring within the service.</span></span> <span data-ttu-id="39d68-106">Další informace o konfiguraci trasování najdete v tématu: [Konfigurace trasování](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="39d68-106">For more information on configuring tracing, see: [Configuring Tracing](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="39d68-107">Další informace o prohlížeči soubor trasování najdete v tématu: [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="39d68-107">For more information on the trace file viewer, see: [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
1.  [<span data-ttu-id="39d68-108">Po instalaci systému Windows 7 a IIS, při pokusu o přejděte do služby WCF zobrazí následující chybová zpráva: HTTP Chyba 404.3 – nebyla nalezena</span><span class="sxs-lookup"><span data-stu-id="39d68-108">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     <span data-ttu-id="39d68-109">Chyba protokolu HTTP 404.3 – není FoundThe stránku nelze zpracovat kvůli konfiguraci rozšíření.</span><span class="sxs-lookup"><span data-stu-id="39d68-109">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="39d68-110">Pokud je stránce skript, přidejte obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="39d68-110">If the page is a script, add a handler.</span></span> <span data-ttu-id="39d68-111">Pokud by měl být soubor stažen, přidejte mapování dat MIME.</span><span class="sxs-lookup"><span data-stu-id="39d68-111">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="39d68-112">Iisver InformationModule podrobné informace o chybě.</span><span class="sxs-lookup"><span data-stu-id="39d68-112">Detailed Error InformationModule StaticFileModule.</span></span>  
  
2.  [<span data-ttu-id="39d68-113">Pokud klient nečinný nějakou dobu, po prvním požadavku se někdy zobrazí messagesecurityexception – na druhý žádosti. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-113">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request. What is happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [<span data-ttu-id="39d68-114">Moje služba začne odmítnout nové klienty po asi 10 klienti komunikují s ním. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-114">My service starts to reject new clients after about 10 clients are interacting with it. What is happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [<span data-ttu-id="39d68-115">Můžete načíst Moje konfigurace služby z jinde, než konfigurační soubor WCF aplikace?</span><span class="sxs-lookup"><span data-stu-id="39d68-115">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [<span data-ttu-id="39d68-116">Moje služba a klient pracovní velká, ale I nelze získat nich mohli pracovat, když se klient nachází v jiném počítači? Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-116">My service and client work great, but I can’t get them to work when the client is on another computer? What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [<span data-ttu-id="39d68-117">I když throw FaultException\<výjimka > typ jsou výjimku, bylo vždycky přijímat obecného typu FaultException na straně klienta a není obecného typu. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-117">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [<span data-ttu-id="39d68-118">Podle všeho jako jednosměrný a operace požadavek odpověď vracet přibližně stejnou rychlostí odpověď neobsahuje žádná data. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-118">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data. What's happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [<span data-ttu-id="39d68-119">Používám certifikát X.509 s mé služby a získat System.Security.Cryptography.CryptographicException. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-119">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [<span data-ttu-id="39d68-120">První parametr operace bylo změněno z velkých písmen na malá písmena; Teď Moje klienta vyvolá výjimku. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-120">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception. What's happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [<span data-ttu-id="39d68-121">Používám jeden z mých trasování nástrojů a získat endpointnotfoundexception –. Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-121">I’m using one of my tracing tools and I get an EndpointNotFoundException. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [<span data-ttu-id="39d68-122">Při volání z aplikace WCF SOAP služby WCF Web HTTP aplikace vrátí následující chybu: není povoleno 405 – Metoda</span><span class="sxs-lookup"><span data-stu-id="39d68-122">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [<span data-ttu-id="39d68-123">Co je základní adresa? Jak vztahují k adresu koncového bodu?</span><span class="sxs-lookup"><span data-stu-id="39d68-123">What is the base address? How does it relate to an endpoint address?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a><span data-ttu-id="39d68-124">Po instalaci systému Windows 7 a IIS, při pokusu o přejděte do služby WCF zobrazí následující chybová zpráva: HTTP Chyba 404.3 – nebyla nalezena</span><span class="sxs-lookup"><span data-stu-id="39d68-124">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>  
 <span data-ttu-id="39d68-125">Je celá chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="39d68-125">The full error message is:</span></span>  
  
 <span data-ttu-id="39d68-126">Chyba protokolu HTTP 404.3 – není FoundThe stránku nelze zpracovat kvůli konfiguraci rozšíření.</span><span class="sxs-lookup"><span data-stu-id="39d68-126">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="39d68-127">Pokud je stránce skript, přidejte obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="39d68-127">If the page is a script, add a handler.</span></span> <span data-ttu-id="39d68-128">Pokud by měl být soubor stažen, přidejte mapování dat MIME.</span><span class="sxs-lookup"><span data-stu-id="39d68-128">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="39d68-129">Iisver InformationModule podrobné informace o chybě.</span><span class="sxs-lookup"><span data-stu-id="39d68-129">Detailed Error InformationModule StaticFileModule.</span></span>  
  
 <span data-ttu-id="39d68-130">Tato chybová zpráva nastane, když "Windows Communication Foundation HTTP aktivace" není explicitně nastavena v Ovládacích panelech.</span><span class="sxs-lookup"><span data-stu-id="39d68-130">This error message occurs when "Windows Communication Foundation HTTP Activation" is not explicitly set in the Control Panel.</span></span> <span data-ttu-id="39d68-131">Nastavit tento přejděte na ovládacích panelech, klikněte v levém dolním rohu okna programy.</span><span class="sxs-lookup"><span data-stu-id="39d68-131">To set this go to the Control Panel, click Programs in the lower left hand corner of the window.</span></span> <span data-ttu-id="39d68-132">Zapnout nebo vypnout, klikněte na možnost zapnout funkce systému Windows.</span><span class="sxs-lookup"><span data-stu-id="39d68-132">Click Turn Windows features on or off.</span></span> <span data-ttu-id="39d68-133">Rozhraní Microsoft .NET Framework 3.5.1 rozbalte a vyberte aktivace Windows Communication Foundation HTTP.</span><span class="sxs-lookup"><span data-stu-id="39d68-133">Expand Microsoft .NET Framework 3.5.1 and select Windows Communication Foundation HTTP Activation.</span></span>  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a><span data-ttu-id="39d68-134">Pokud klient nečinný nějakou dobu, po prvním požadavku se někdy zobrazí messagesecurityexception – na druhý žádosti.</span><span class="sxs-lookup"><span data-stu-id="39d68-134">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request.</span></span> <span data-ttu-id="39d68-135">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-135">What is happening?</span></span>  
 <span data-ttu-id="39d68-136">Druhá žádost neúspěšně především dvou důvodů: Vypršel časový limit relace (1) nebo (2) je webový server, který je hostitelem služby je recykluje.</span><span class="sxs-lookup"><span data-stu-id="39d68-136">The second request can fail primarily for two reasons: (1) the session has timed out or (2) the Web server that is hosting the service is recycled.</span></span> <span data-ttu-id="39d68-137">V prvním případě relace je platný, dokud služba vyprší časový limit. Když službu neobdrží žádost od klienta v rámci doba zadaná v vazby služby (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), služba ukončuje relaci zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="39d68-137">In the first case, the session is valid until the service times out. When the service does not receive a request from the client within the period of time specified in the service's binding (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), the service terminates the security session.</span></span> <span data-ttu-id="39d68-138">Výsledkem zprávy následné klienta <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="39d68-138">Subsequent client messages result in the <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="39d68-139">Klient musí znovu vytvořit relaci zabezpečené službou odeslat další zprávy nebo použijte tokenu kontextu stavová zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="39d68-139">The client must re-establish a secure session with the service to send future messages or use a stateful security context token.</span></span> <span data-ttu-id="39d68-140">Tokeny kontextu zabezpečení stavová také povolit zabezpečené relace zůstanou zachovány i recyklovány webového serveru.</span><span class="sxs-lookup"><span data-stu-id="39d68-140">Stateful security context tokens also allow a secure session to survive a Web server being recycled.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="39d68-141">pomocí tokenů stavová kontextu zabezpečení v zabezpečené relaci, najdete v tématu [postupy: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="39d68-141"> using stateful secure context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span> <span data-ttu-id="39d68-142">Alternativně můžete zakázat zabezpečených relací.</span><span class="sxs-lookup"><span data-stu-id="39d68-142">Alternatively, you can disable secure sessions.</span></span> <span data-ttu-id="39d68-143">Při použití [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) vazby, můžete nastavit `establishSecurityContext` vlastnost `false` zakázání zabezpečených relací.</span><span class="sxs-lookup"><span data-stu-id="39d68-143">When you use the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) binding, you can set the `establishSecurityContext` property to `false` to disable secure sessions.</span></span> <span data-ttu-id="39d68-144">Zakázání zabezpečených relací u dalších vazeb, musíte vytvořit vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="39d68-144">To disable secure sessions for other bindings, you must create a custom binding.</span></span> <span data-ttu-id="39d68-145">Podrobnosti o vytváření vlastních vazeb najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="39d68-145">For details about creating a custom binding, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="39d68-146">Než použijete některý z těchto možností, musíte pochopit požadavky na zabezpečení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="39d68-146">Before you apply any of these options, you must understand your application's security requirements.</span></span>  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a><span data-ttu-id="39d68-147">Moje služba začne odmítnout nové klienty po asi 10 klienti komunikují s ním.</span><span class="sxs-lookup"><span data-stu-id="39d68-147">My service starts to reject new clients after about 10 clients are interacting with it.</span></span> <span data-ttu-id="39d68-148">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-148">What is happening?</span></span>  
 <span data-ttu-id="39d68-149">Ve výchozím nastavení služby může mít jenom 10 souběžných relací.</span><span class="sxs-lookup"><span data-stu-id="39d68-149">By default, services can have only 10 concurrent sessions.</span></span> <span data-ttu-id="39d68-150">Proto pokud vazby služby použít relací, služba přijímá nová připojení klienta dokud nedosáhne počet, po jejímž uplynutí odmítne nová připojení klienta až jeden z konců aktuální relace.</span><span class="sxs-lookup"><span data-stu-id="39d68-150">Therefore, if the service bindings use sessions, the service accepts new client connections until it reaches that number, after which it refuses new client connections until one of the current sessions ends.</span></span> <span data-ttu-id="39d68-151">Může podporovat více klientů v několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="39d68-151">You can support more clients in a number of ways.</span></span> <span data-ttu-id="39d68-152">Pokud vaše služba nevyžaduje relací, nepoužívejte vazbu relacemi.</span><span class="sxs-lookup"><span data-stu-id="39d68-152">If your service does not require sessions, do not use a sessionful binding.</span></span> <span data-ttu-id="39d68-153">([!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Použití relací](../../../docs/framework/wcf/using-sessions.md).) Další možností je zvýšení limitu relace tak, že změníte hodnotu <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> vlastnost na číslo, které jsou vhodné pro vaše okolnosti.</span><span class="sxs-lookup"><span data-stu-id="39d68-153">([!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Using Sessions](../../../docs/framework/wcf/using-sessions.md).) Another option is to increase the session limit by changing the value of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> property to the number appropriate to your circumstance.</span></span>  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a><span data-ttu-id="39d68-154">Můžete načíst Moje konfigurace služby z jinde, než konfigurační soubor WCF aplikace?</span><span class="sxs-lookup"><span data-stu-id="39d68-154">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>  
 <span data-ttu-id="39d68-155">Ano, ale je nutné vytvořit vlastní <xref:System.ServiceModel.ServiceHost> třídu, která přepisuje <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="39d68-155">Yes, however, you have to create a custom <xref:System.ServiceModel.ServiceHost> class that overrides the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method.</span></span> <span data-ttu-id="39d68-156">Uvnitř této metody můžete volat základní nejdřív načíst konfiguraci (Pokud chcete načíst informace o standardní konfiguraci i), ale můžete také úplně nahradit konfigurace načítání systému.</span><span class="sxs-lookup"><span data-stu-id="39d68-156">Inside that method, you can call the base to load configuration first (if you want to load the standard configuration information as well) but you can also entirely replace the configuration loading system.</span></span> <span data-ttu-id="39d68-157">Všimněte si, že pokud chcete načíst konfiguraci z konfiguračního souboru, který se liší od konfiguračního souboru aplikace, musíte analyzovat konfigurační soubor a načíst konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="39d68-157">Note that if you want to load configuration from a configuration file that is different from the application configuration file, you must parse the configuration file yourself and load the configuration.</span></span>  
  
 <span data-ttu-id="39d68-158">Následující příklad kódu ukazuje, jak lze přepsat <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> metoda a přímo konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="39d68-158">The following code example shows how to override the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method and directly configure an endpoint.</span></span>  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a><span data-ttu-id="39d68-159">Moje služba a klient pracovní velká, ale I nelze získat nich mohli pracovat, když se klient nachází v jiném počítači?</span><span class="sxs-lookup"><span data-stu-id="39d68-159">My service and client work great, but I can’t get them to work when the client is on another computer?</span></span> <span data-ttu-id="39d68-160">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-160">What’s happening?</span></span>  
 <span data-ttu-id="39d68-161">V závislosti na výjimku, může existovat několik výhrad:</span><span class="sxs-lookup"><span data-stu-id="39d68-161">Depending upon the exception, there may be several issues:</span></span>  
  
-   <span data-ttu-id="39d68-162">Možná budete muset změňte adresy koncových bodů klienta na název hostitele a není "localhost".</span><span class="sxs-lookup"><span data-stu-id="39d68-162">You might need to change the client endpoint addresses to the host name and not "localhost".</span></span>  
  
-   <span data-ttu-id="39d68-163">Možná budete muset otevřít port, který se aplikace.</span><span class="sxs-lookup"><span data-stu-id="39d68-163">You might need to open the port to the application.</span></span> <span data-ttu-id="39d68-164">Podrobnosti najdete v tématu [pokyny k bráně Firewall](../../../docs/framework/wcf/samples/firewall-instructions.md) z ukázky SDK.</span><span class="sxs-lookup"><span data-stu-id="39d68-164">For details, see [Firewall Instructions](../../../docs/framework/wcf/samples/firewall-instructions.md) from the SDK samples.</span></span>  
  
-   <span data-ttu-id="39d68-165">Další možných problémů naleznete v tématu ukázky [spuštění ukázky v pracovní skupině a počítačů přes](http://msdn.microsoft.com/en-us/a451a525-e7ce-452d-9da9-620221260113).</span><span class="sxs-lookup"><span data-stu-id="39d68-165">For other possible issues, see the samples topic [Running the Samples in a Workgroup and Across Machines](http://msdn.microsoft.com/en-us/a451a525-e7ce-452d-9da9-620221260113).</span></span>  
  
-   <span data-ttu-id="39d68-166">Pokud je váš klient je pomocí pověření systému Windows a výjimky <xref:System.ServiceModel.Security.SecurityNegotiationException>, následujícím způsobem konfigurace protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="39d68-166">If your client is using Windows credentials and the exception is a <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure Kerberos as follows.</span></span>  
  
    1.  <span data-ttu-id="39d68-167">Přidejte tato pověření identity do koncového bodu element v souboru App.config klienta:</span><span class="sxs-lookup"><span data-stu-id="39d68-167">Add the identity credentials to the endpoint element in the client’s App.config file:</span></span>  
  
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
  
    2.  <span data-ttu-id="39d68-168">Spusťte službu vlastním hostováním pod účtem systému nebo NetworkService.</span><span class="sxs-lookup"><span data-stu-id="39d68-168">Run the self-hosted service under the System or NetworkService account.</span></span> <span data-ttu-id="39d68-169">Můžete spustit tento příkaz k vytvoření příkazové okno pod účtem System:</span><span class="sxs-lookup"><span data-stu-id="39d68-169">You can run this command to create a command window under the System account:</span></span>  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  <span data-ttu-id="39d68-170">Hostování v části Internetovou informační služby (IIS), což, standardně používá účet služby (SPN) pro hlavní název služby.</span><span class="sxs-lookup"><span data-stu-id="39d68-170">Host the service under Internet Information Services (IIS), which, by default, uses the service principal name (SPN) account.</span></span>  
  
    4.  <span data-ttu-id="39d68-171">Zaregistrujte novou hlavního názvu služby k doméně pomocí nástroje SetSPN.</span><span class="sxs-lookup"><span data-stu-id="39d68-171">Register a new SPN with the domain using SetSPN.</span></span> <span data-ttu-id="39d68-172">Všimněte si, že musíte být správce domény, pokud to chcete provést.</span><span class="sxs-lookup"><span data-stu-id="39d68-172">Note that you will need to be a domain administrator in order to do this.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="39d68-173">protokol Kerberos najdete v části [zabezpečení koncepty používané ve službě WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) a:</span><span class="sxs-lookup"><span data-stu-id="39d68-173"> the Kerberos protocol, see [Security Concepts Used in WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) and:</span></span>  
  
-   [<span data-ttu-id="39d68-174">Ladění chyb ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="39d68-174">Debugging Windows Authentication Errors</span></span>](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [<span data-ttu-id="39d68-175">Registrace pomocí ovladače Http.sys hlavní názvy služby protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="39d68-175">Registering Kerberos Service Principal Names by Using Http.sys</span></span>](http://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [<span data-ttu-id="39d68-176">Vysvětlení protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="39d68-176">Kerberos Explained</span></span>](http://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a><span data-ttu-id="39d68-177">I když throw FaultException\<výjimka > typ jsou výjimku, bylo vždycky přijímat obecného typu FaultException na straně klienta a není obecného typu.</span><span class="sxs-lookup"><span data-stu-id="39d68-177">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type.</span></span> <span data-ttu-id="39d68-178">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-178">What’s happening?</span></span>  
 <span data-ttu-id="39d68-179">Důrazně doporučujeme, abyste vytvořili vlastní vlastní chybové datový typ a prohlásí, že jako typ podrobností v vaše chyba – kontrakt.</span><span class="sxs-lookup"><span data-stu-id="39d68-179">It is highly recommended that you create your own custom error data type and declare that as the detail type in your fault contract.</span></span> <span data-ttu-id="39d68-180">Důvodem je, že použití typů poskytované systémem výjimka:</span><span class="sxs-lookup"><span data-stu-id="39d68-180">The reason is that using system-provided exception types:</span></span>  
  
-   <span data-ttu-id="39d68-181">Vytvoří závislost na typ, který odebere jeden z největších výhod aplikace orientované na služby.</span><span class="sxs-lookup"><span data-stu-id="39d68-181">Creates a type dependency that removes one of the biggest strengths of service-oriented applications.</span></span>  
  
-   <span data-ttu-id="39d68-182">Nelze závisí na výjimky serializaci standardním způsobem.</span><span class="sxs-lookup"><span data-stu-id="39d68-182">Cannot depend upon exceptions serializing in a standard way.</span></span> <span data-ttu-id="39d68-183">Některé – jako <xref:System.Security.SecurityException>– nemusí být serializovatelný vůbec.</span><span class="sxs-lookup"><span data-stu-id="39d68-183">Some—like <xref:System.Security.SecurityException>—may not be serializable at all.</span></span>  
  
-   <span data-ttu-id="39d68-184">Zpřístupní podrobnosti interní implementace klientům.</span><span class="sxs-lookup"><span data-stu-id="39d68-184">Exposes internal implementation details to clients.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="39d68-185">[Určování a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="39d68-185"> [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
 <span data-ttu-id="39d68-186">Pokud ladíte aplikaci, ale může serializovat informace o výjimce a vrátí klientovi pomocí <xref:System.ServiceModel.Description.ServiceDebugBehavior> třídy.</span><span class="sxs-lookup"><span data-stu-id="39d68-186">If you are debugging an application, however, you can serialize exception information and return it to the client by using the <xref:System.ServiceModel.Description.ServiceDebugBehavior> class.</span></span>  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a><span data-ttu-id="39d68-187">Podle všeho jako jednosměrný a operace požadavek odpověď vracet přibližně stejnou rychlostí odpověď neobsahuje žádná data.</span><span class="sxs-lookup"><span data-stu-id="39d68-187">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data.</span></span> <span data-ttu-id="39d68-188">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-188">What's happening?</span></span>  
 <span data-ttu-id="39d68-189">Určení, že operace je jedním ze způsobů pouze znamená, že operace kontrakt přijímá zprávy při zadávání a nevrací zprávu výstup.</span><span class="sxs-lookup"><span data-stu-id="39d68-189">Specifying that an operation is one way means only that the operation contract accepts an input message and does not return an output message.</span></span> <span data-ttu-id="39d68-190">V [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], všechna volání vrátí, když se odchozí data byla zapsána na sítě, nebo je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="39d68-190">In [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], all client invocations return when the outbound data has been written to the wire or an exception is thrown.</span></span> <span data-ttu-id="39d68-191">Jednosměrná operace fungují stejně a můžete vyvolají, pokud služba nemůže najít nebo blokovat, pokud služba není připraven na příjem dat ze sítě.</span><span class="sxs-lookup"><span data-stu-id="39d68-191">One-way operations work the same way, and they can throw if the service cannot be located or block if the service is not prepared to accept the data from the network.</span></span> <span data-ttu-id="39d68-192">Obvykle v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], výsledkem je jednosměrný volání vrácením klientovi rychleji než požadavek odpověď; ale žádné podmínku, která zpomalí odesílání odchozí data v síti zpomalí Jednosměrná operace, jakož i operace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="39d68-192">Typically in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], this results in one-way calls returning to the client more quickly than request-reply; but any condition that slows the sending of the outbound data over the network slows one-way operations as well as request-reply operations.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="39d68-193">[Jednosměrné služby](../../../docs/framework/wcf/feature-details/one-way-services.md) a [přístup ke službám pomocí klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).</span><span class="sxs-lookup"><span data-stu-id="39d68-193"> [One-Way Services](../../../docs/framework/wcf/feature-details/one-way-services.md) and [Accessing Services Using a WCF Client](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).</span></span>  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a><span data-ttu-id="39d68-194">Používám certifikát X.509 s mé služby a získat System.Security.Cryptography.CryptographicException.</span><span class="sxs-lookup"><span data-stu-id="39d68-194">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException.</span></span> <span data-ttu-id="39d68-195">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-195">What’s happening?</span></span>  
 <span data-ttu-id="39d68-196">K tomu obvykle dochází po změně uživatelský účet, pod kterým služba IIS pracovní proces běží.</span><span class="sxs-lookup"><span data-stu-id="39d68-196">This commonly occurs after changing the user account under which the IIS worker process runs.</span></span> <span data-ttu-id="39d68-197">Například v [!INCLUDE[wxp](../../../includes/wxp-md.md)], pokud změníte výchozí uživatelský účet, který Aspnet_wp.exe spouští pod z ASPNET na vlastní uživatelský účet, se zobrazí tato chyba.</span><span class="sxs-lookup"><span data-stu-id="39d68-197">For example, in [!INCLUDE[wxp](../../../includes/wxp-md.md)], if you change the default user account that the Aspnet_wp.exe runs under from ASPNET to a custom user account, you may see this error.</span></span> <span data-ttu-id="39d68-198">Pokud používáte privátní klíč, proces, který používá je potřeba mít oprávnění pro přístup k souboru ukládání klíči.</span><span class="sxs-lookup"><span data-stu-id="39d68-198">If using a private key, the process that uses it will need to have permissions to access the file storing that key.</span></span>  
  
 <span data-ttu-id="39d68-199">Pokud je to tento případ, musí udělit přístup pro čtení oprávnění k účtu procesu pro soubor obsahující privátní klíč.</span><span class="sxs-lookup"><span data-stu-id="39d68-199">If this is the case, you must give read access privileges to the process's account for the file containing the private key.</span></span> <span data-ttu-id="39d68-200">Například pokud pracovní proces služby IIS běží pod účtem Bob, pak musíte poskytnout přístup pro čtení Bob k souboru, který obsahuje soukromý klíč.</span><span class="sxs-lookup"><span data-stu-id="39d68-200">For example, if the IIS worker process is running under the Bob account, then you will need to give Bob read access to the file containing the private key.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="39d68-201">jak poskytnout správné uživatelský účet přístup k souboru, který obsahuje soukromý klíč pro konkrétní certifikát X.509, najdete v části [postup: usnadnit X.509 certifikáty přístup do WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="39d68-201"> how to give the correct user account access to the file that contains the private key for a specific X.509 certificate, see [How to: Make X.509 Certificates Accessible to WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span></span>  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a><span data-ttu-id="39d68-202">První parametr operace bylo změněno z velkých písmen na malá písmena; Teď Moje klienta vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="39d68-202">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception.</span></span> <span data-ttu-id="39d68-203">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-203">What's happening?</span></span>  
 <span data-ttu-id="39d68-204">Hodnota názvy parametrů v podpis operace jsou součástí kontraktu a malých a velkých písmen.</span><span class="sxs-lookup"><span data-stu-id="39d68-204">The value of the parameter names in the operation signature are part of the contract and are case-sensitive.</span></span> <span data-ttu-id="39d68-205">Použití <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> atribut až budete potřebovat k rozlišení názvu parametru místní a metadata, která popisuje operaci pro klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="39d68-205">Use the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> attribute when you need to distinguish between the local parameter name and the metadata that describes the operation for client applications.</span></span>  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a><span data-ttu-id="39d68-206">Používám jeden z mých trasování nástrojů a získat endpointnotfoundexception –.</span><span class="sxs-lookup"><span data-stu-id="39d68-206">I’m using one of my tracing tools and I get an EndpointNotFoundException.</span></span> <span data-ttu-id="39d68-207">Co se děje?</span><span class="sxs-lookup"><span data-stu-id="39d68-207">What’s happening?</span></span>  
 <span data-ttu-id="39d68-208">Pokud používáte nástroj trasování, který není poskytované systémem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] mechanismus trasování a zobrazí se <xref:System.ServiceModel.EndpointNotFoundException> určující, že došlo neshodě adres filtru, budete muset použít <xref:System.ServiceModel.Description.ClientViaBehavior> třída směrovat zprávy, které mají trasování nástroje a mít nástroj přesměruje tyto zprávy na adresu služby.</span><span class="sxs-lookup"><span data-stu-id="39d68-208">If you are using a tracing tool that is not the system-provided [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] tracing mechanism and you receive an <xref:System.ServiceModel.EndpointNotFoundException> that indicates that there was an address filter mismatch, you need to use the <xref:System.ServiceModel.Description.ClientViaBehavior> class to direct the messages to the tracing utility and have the utility redirect those messages to the service address.</span></span> <span data-ttu-id="39d68-209"><xref:System.ServiceModel.Description.ClientViaBehavior> Třída mění `Via` indikován adresování záhlaví zadat další síťová adresa odděleně od ultimate příjemce, `To` adresování záhlaví.</span><span class="sxs-lookup"><span data-stu-id="39d68-209">The <xref:System.ServiceModel.Description.ClientViaBehavior> class alters the `Via` addressing header to specify the next network address separately from the ultimate receiver, indicated by the `To` addressing header.</span></span> <span data-ttu-id="39d68-210">Pokud v takovém případě však neměňte adresa koncového bodu, který se používá k navázání `To` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="39d68-210">When doing this, however, do not change the endpoint address, which is used to establish the `To` value.</span></span>  
  
 <span data-ttu-id="39d68-211">Následující příklad kódu ukazuje klientem příklad konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="39d68-211">The following code example shows an example client configuration file.</span></span>  
  
```xml
<endpoint   
  address=http://localhost:8000/MyServer/  
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
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a><span data-ttu-id="39d68-212">Co je základní adresa?</span><span class="sxs-lookup"><span data-stu-id="39d68-212">What is the base address?</span></span> <span data-ttu-id="39d68-213">Jak vztahují k adresu koncového bodu?</span><span class="sxs-lookup"><span data-stu-id="39d68-213">How does it relate to an endpoint address?</span></span>  
 <span data-ttu-id="39d68-214">Základní adresa je adresa kořenové pro <xref:System.ServiceModel.ServiceHost> třídy.</span><span class="sxs-lookup"><span data-stu-id="39d68-214">A base address is the root address for a <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="39d68-215">Ve výchozím nastavení, pokud přidáte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy do konfigurace služby webové služby popis Language (WSDL) pro hostitele publikuje všechny koncové body jsou načteny z základní adresu HTTP plus všechny relativní adresa zadaná v chování metadat plus "? wsdl".</span><span class="sxs-lookup"><span data-stu-id="39d68-215">By default, if you add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class into your service configuration, the Web Services Description Language (WSDL) for all endpoints the host publishes are retrieved from the HTTP base address, plus any relative address provided to the metadata behavior, plus "?wsdl".</span></span> <span data-ttu-id="39d68-216">Pokud jste se seznámili s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] a služby IIS, základní adresa je ekvivalentní do virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="39d68-216">If you are familiar with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] and IIS, the base address is equivalent to the virtual directory.</span></span>  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a><span data-ttu-id="39d68-217">Sdílení portů mezi koncového bodu služby a koncový bod mex pomocí NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="39d68-217">Sharing a port between a service endpoint and a mex endpoint using the NetTcpBinding</span></span>  
 <span data-ttu-id="39d68-218">Pokud zadáte adresu základní pro služby jako net.tcp://MyServer: 8080/Moje_služba a přidejte následující koncové body:</span><span class="sxs-lookup"><span data-stu-id="39d68-218">If you specify the base address for a service as net.tcp://MyServer:8080/MyService and add the following endpoints:</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="39d68-219">A pokud změníte jedno z nastavení NetTcpBinding jak je znázorněno v následujícím fragmentu kódu konfigurace:</span><span class="sxs-lookup"><span data-stu-id="39d68-219">And if you modify one of the NetTcpBinding settings as shown in the following configuration snippet:</span></span>  
  
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
  
 <span data-ttu-id="39d68-220">Zobrazí se chyba takto: neošetřená výjimka: System.ServiceModel.AddressAlreadyInUseException: na 0.0.0.0:9000 koncový bod IP tuto chybu můžete vyřešit tak, že zadáte plně kvalifikovanou adresu URL s jiným portem pro je již naslouchací proces MEX endpoint, jak je znázorněno v následujícím fragmentu kódu konfigurace:</span><span class="sxs-lookup"><span data-stu-id="39d68-220">You will see an error like the following: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000 You can work around this error by specifying a fully qualified URL with a different port for the MEX endpoint as shown in the following configuration snippet:</span></span>  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a><span data-ttu-id="39d68-221">Při volání z aplikace WCF SOAP služby WCF Web HTTP aplikace vrátí následující chybu: není povoleno 405 – Metoda</span><span class="sxs-lookup"><span data-stu-id="39d68-221">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>  
 <span data-ttu-id="39d68-222">Volání aplikace WCF Web HTTP (služba, která využívá <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior>) z službou WCF služba může generovat následující výjimky: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: vzdálený server vrátil neočekávanou odpověď : (405) metoda není povoleno. ", protože WCF přepíše odchozích došlo k této výjimce <xref:System.ServiceModel.OperationContext> s příchozí <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="39d68-222">Calling a WCF Web HTTP application (a service that uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior>) from a WCF service may generate the following exception: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.\` This exception occurs because WCF overwrites the outgoing <xref:System.ServiceModel.OperationContext> with the incoming <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="39d68-223">Chcete-li vyřešit tento problém vytvořit <xref:System.ServiceModel.OperationContextScope> v rámci operace služby WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="39d68-223">To solve this problem create an <xref:System.ServiceModel.OperationContextScope> within the WCF Web HTTP service operation.</span></span> <span data-ttu-id="39d68-224">Příklad:</span><span class="sxs-lookup"><span data-stu-id="39d68-224">For example:</span></span>  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="39d68-225">Viz také</span><span class="sxs-lookup"><span data-stu-id="39d68-225">See Also</span></span>  
 [<span data-ttu-id="39d68-226">Ladění chyb ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="39d68-226">Debugging Windows Authentication Errors</span></span>](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)

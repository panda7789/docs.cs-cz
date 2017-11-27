---
title: "Otázky zabezpečení a užitečné tipy pro trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 07ac814253a563a0cbdad1014970af3d18c6fdde
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="af448-102">Otázky zabezpečení a užitečné tipy pro trasování</span><span class="sxs-lookup"><span data-stu-id="af448-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="af448-103">Toto téma popisuje, jak můžete chránit citlivé informace před vystavením i užitečné tipy, při použití webového hostitele.</span><span class="sxs-lookup"><span data-stu-id="af448-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="af448-104">Vlastní naslouchací pomocí webového hostitele</span><span class="sxs-lookup"><span data-stu-id="af448-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="af448-105">Pokud píšete vlastní naslouchací proces trasování, byste měli vědět o možnosti, že trasování může dojít ke ztrátě v případě hostované webové služby.</span><span class="sxs-lookup"><span data-stu-id="af448-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="af448-106">Recyklování tomuto webovému hostiteli vypne proces za provozu při převezme duplicitní.</span><span class="sxs-lookup"><span data-stu-id="af448-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="af448-107">Však dva procesy však musí mít přístup do stejného zdroje nějakou dobu, což závisí na typu naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="af448-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="af448-108">V takovém případě, `XmlWriterTraceListener` vytvoří nový soubor trasování pro proces druhý; při trasování událostí pro Windows spravuje více procesy v rámci stejné relace a poskytuje přístup ke stejnému souboru.</span><span class="sxs-lookup"><span data-stu-id="af448-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="af448-109">Pokud vlastní naslouchací proces neposkytuje podobné funkce, trasování může být ztracena, pokud je soubor uzamčen dva procesy.</span><span class="sxs-lookup"><span data-stu-id="af448-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="af448-110">Byste měli taky vědět, že vlastní naslouchací může poslat trasování a zprávy v drátové síti, například ke vzdálené databázi.</span><span class="sxs-lookup"><span data-stu-id="af448-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="af448-111">Jako modul pro nasazení aplikace měli byste nakonfigurovat vlastní naslouchací procesy s ovládacím prvkem odpovídající přístup.</span><span class="sxs-lookup"><span data-stu-id="af448-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="af448-112">Také byste měli použít řízení zabezpečení na všechny osobní informace, které mohou být zpřístupněny ve vzdáleném umístění.</span><span class="sxs-lookup"><span data-stu-id="af448-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="af448-113">Protokolování citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="af448-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="af448-114">Trasování obsahovat hlavičky zpráv, pokud zpráva je v oboru.</span><span class="sxs-lookup"><span data-stu-id="af448-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="af448-115">Pokud je trasování povoleno, osobní údaje v hlavičkách specifické pro aplikace, jako je řetězec dotazu; a body informace, například číslo platební karty, se může stát viditelné v protokolech.</span><span class="sxs-lookup"><span data-stu-id="af448-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="af448-116">Nástroje pro nasazení aplikace je zodpovědná za prosadit řízení přístupu na soubory konfigurace a trasování.</span><span class="sxs-lookup"><span data-stu-id="af448-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="af448-117">Pokud nechcete, aby tento druh informací viditelný, si zakázat trasování nebo odfiltrovat část dat, pokud chcete sdílet protokolů trasování.</span><span class="sxs-lookup"><span data-stu-id="af448-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="af448-118">Následující tipy vám může pomoct zabránit neúmyslnému zveřejnění obsahu souboru trasování:</span><span class="sxs-lookup"><span data-stu-id="af448-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
-   <span data-ttu-id="af448-119">Zajistěte, aby v protokolu, které soubory jsou chráněné pomocí řízení přístupu jsou uvedené (ACL) v webového hostitele i scénáře hostování na vlastním serveru.</span><span class="sxs-lookup"><span data-stu-id="af448-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
-   <span data-ttu-id="af448-120">Zvolte příponu souboru, který nelze zpracovat snadno pomocí nějaké webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="af448-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="af448-121">Například přípona souboru .xml není bezpečná volba.</span><span class="sxs-lookup"><span data-stu-id="af448-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="af448-122">Můžete zkontrolovat v Průvodci správy služby IIS najdete v části Seznam přípon, které se dají obsluhovat.</span><span class="sxs-lookup"><span data-stu-id="af448-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
-   <span data-ttu-id="af448-123">Zadejte absolutní cestu k umístění souboru protokolu, které by měla být mimo adresář veřejné vroot webového hostitele, který chcete zabránit přistupuje externí strany pomocí webového prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="af448-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="af448-124">Ve výchozím nastavení klíče a identifikovatelné osobní údaje (PII), jako je například uživatelské jméno a heslo nejsou protokolovány v trasování a protokolovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="af448-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="af448-125">Správce počítače, ale můžete použít `enableLoggingKnownPII` atribut `machineSettings` element souboru Machine.config tak, aby povolovala aplikace spuštěna v počítači do protokolu známé identifikovatelné osobní údaje (PII) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="af448-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>   
```  
  
 <span data-ttu-id="af448-126">Pak můžete použít modul pro nasazení aplikace `logKnownPii` atribut v souboru App.config nebo Web.config povolení protokolování PII následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="af448-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="af448-127">Pouze, pokud jsou obě nastavení `true` je povoleno protokolování PII.</span><span class="sxs-lookup"><span data-stu-id="af448-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="af448-128">Kombinace dva přepínače umožňuje flexibilně protokolu známé PII pro každou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="af448-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="af448-129">Je třeba si uvědomit, že pokud zadáte dva nebo více vlastních zdrojů v konfiguračním souboru, se čtou jenom atributy první zdroje.</span><span class="sxs-lookup"><span data-stu-id="af448-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="af448-130">Další se ignorují.</span><span class="sxs-lookup"><span data-stu-id="af448-130">The others are ignored.</span></span> <span data-ttu-id="af448-131">To znamená, že pro následující App.config souboru PII se neprotokolují pro oba zdroje i když druhý zdroj je výslovně povoleno protokolování PII.</span><span class="sxs-lookup"><span data-stu-id="af448-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="false">  
        <listeners>  
           <add name="messages"  
                type="System.Diagnostics.XmlWriterTraceListener"  
                initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
      <source name="System.ServiceModel"   
         logKnownPii="true">  
         <listeners>  
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="af448-132">Pokud `<machineSettings enableLoggingKnownPii="Boolean"/>` element existuje mimo souboru Machine.config, vyvolá systému <xref:System.Configuration.ConfigurationErrorsException>.</span><span class="sxs-lookup"><span data-stu-id="af448-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="af448-133">Změny jsou platné jenom v případě, že spuštění nebo restartování aplikace.</span><span class="sxs-lookup"><span data-stu-id="af448-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="af448-134">Při spuštění se zaprotokoluje událost, když oba atributy jsou nastaveny na `true`.</span><span class="sxs-lookup"><span data-stu-id="af448-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="af448-135">Pokud se taky zaznamená událost `logKnownPii` je nastaven na `true` ale `enableLoggingKnownPii` je `false`.</span><span class="sxs-lookup"><span data-stu-id="af448-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="af448-136">Další informace o protokolování PII najdete v tématu [bezpečnostní uzamčení PII](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="af448-136">For more information on PII logging, see [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="af448-137">Správce počítače a nástroje pro nasazení aplikace by měla vykonávat extrémně opatrní při používání těchto dva přepínače.</span><span class="sxs-lookup"><span data-stu-id="af448-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="af448-138">Pokud je povoleno protokolování PII, jsou protokolovány zabezpečení klíčů a PII.</span><span class="sxs-lookup"><span data-stu-id="af448-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="af448-139">Pokud je zakázaná, specifické pro aplikaci a citlivá data protokolovány v záhlaví zprávy a obsah.</span><span class="sxs-lookup"><span data-stu-id="af448-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="af448-140">Podrobnější informace o ochraně osobních údajů a ochrana PII vystavení, naleznete v [ochraně osobních údajů uživatelů](http://go.microsoft.com/fwlink/?LinkID=94647).</span><span class="sxs-lookup"><span data-stu-id="af448-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](http://go.microsoft.com/fwlink/?LinkID=94647).</span></span>  
  
 <span data-ttu-id="af448-141">Kromě toho je IP adresa odesílatele zprávy protokolována jednou za připojení pro přenosy orientovaná na připojení a jednou za zprávou odeslanou v opačném případě.</span><span class="sxs-lookup"><span data-stu-id="af448-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="af448-142">To se provádí bez souhlasu odesílatele.</span><span class="sxs-lookup"><span data-stu-id="af448-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="af448-143">Však protokolování dochází pouze na nebo podrobné informace o úrovních trasování, které nejsou výchozí nebo doporučená úrovní trasování v produkčním prostředí, s výjimkou live ladění.</span><span class="sxs-lookup"><span data-stu-id="af448-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af448-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="af448-144">See Also</span></span>  
 [<span data-ttu-id="af448-145">Trasování</span><span class="sxs-lookup"><span data-stu-id="af448-145">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)

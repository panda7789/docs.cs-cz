---
title: Otázky zabezpečení a užitečné tipy pro trasování
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 5ced4f3a3a5e83564703db88b28ee2b3c6eeb1a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185711"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="a90ee-102">Otázky zabezpečení a užitečné tipy pro trasování</span><span class="sxs-lookup"><span data-stu-id="a90ee-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="a90ee-103">Toto téma popisuje, jak můžete chránit citlivé informace před vystavením, stejně jako užitečné tipy při používání WebHost.</span><span class="sxs-lookup"><span data-stu-id="a90ee-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="a90ee-104">Použití vlastního naslouchací procestras s WebHost</span><span class="sxs-lookup"><span data-stu-id="a90ee-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="a90ee-105">Pokud píšete vlastní naslouchací proces trasování, měli byste si být vědomi možnosti, že trasování může dojít ke ztrátě v případě služby hostované na webu.</span><span class="sxs-lookup"><span data-stu-id="a90ee-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="a90ee-106">Když WebHost recykluje, vypne živý proces, zatímco duplicitní převezme.</span><span class="sxs-lookup"><span data-stu-id="a90ee-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="a90ee-107">Oba procesy však musí mít stále přístup ke stejnému prostředku po určitou dobu, což je závislé na typu naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="a90ee-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="a90ee-108">V tomto případě `XmlWriterTraceListener` , vytvoří nový soubor trasování pro druhý proces; zatímco trasování událostí systému Windows spravuje více procesů v rámci stejné relace a poskytuje přístup ke stejnému souboru.</span><span class="sxs-lookup"><span data-stu-id="a90ee-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="a90ee-109">Pokud vlastní naslouchací proces neposkytuje podobné funkce, trasování může být ztracena, když je soubor uzamčen dvěma procesy.</span><span class="sxs-lookup"><span data-stu-id="a90ee-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="a90ee-110">Měli byste si také být vědomi toho, že vlastní naslouchací proces trasování můžete odesílat trasování a zprávy na lince, například do vzdálené databáze.</span><span class="sxs-lookup"><span data-stu-id="a90ee-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="a90ee-111">Jako nasazovač aplikací byste měli nakonfigurovat vlastní naslouchací procesy s příslušným řízením přístupu.</span><span class="sxs-lookup"><span data-stu-id="a90ee-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="a90ee-112">Měli byste také použít ovládací prvek zabezpečení pro všechny osobní informace, které mohou být vystaveny na vzdáleném místě.</span><span class="sxs-lookup"><span data-stu-id="a90ee-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="a90ee-113">Protokolování citlivých informací</span><span class="sxs-lookup"><span data-stu-id="a90ee-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="a90ee-114">Trasování obsahují záhlaví zpráv, pokud je zpráva v oboru.</span><span class="sxs-lookup"><span data-stu-id="a90ee-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="a90ee-115">Je-li vektorizace povolena, osobní informace v záhlavích specifických pro aplikaci, například v řetězci dotazu; a informace o těle, jako je číslo kreditní karty, mohou být viditelné v protokolech.</span><span class="sxs-lookup"><span data-stu-id="a90ee-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="a90ee-116">Nasazovač aplikací je zodpovědný za vynucení řízení přístupu na konfigurační a trasovací soubory.</span><span class="sxs-lookup"><span data-stu-id="a90ee-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="a90ee-117">Pokud nechcete, aby byl tento druh informací viditelný, měli byste zakázat trasování nebo odfiltrovat část dat, pokud chcete sdílet protokoly trasování.</span><span class="sxs-lookup"><span data-stu-id="a90ee-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="a90ee-118">Následující tipy vám mohou pomoci zabránit neúmyslnému vystavení obsahu trasovacího souboru:</span><span class="sxs-lookup"><span data-stu-id="a90ee-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
- <span data-ttu-id="a90ee-119">Ujistěte se, že soubory protokolu jsou chráněny seznamy řízení přístupu (ACL) ve scénářích WebHost i self-host.</span><span class="sxs-lookup"><span data-stu-id="a90ee-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
- <span data-ttu-id="a90ee-120">Zvolte příponu souboru, kterou nelze snadno obsluhovat pomocí webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="a90ee-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="a90ee-121">Například přípona souboru XML není bezpečnou volbou.</span><span class="sxs-lookup"><span data-stu-id="a90ee-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="a90ee-122">V průvodci správou iis najdete seznam rozšíření, která lze obsluhovat.</span><span class="sxs-lookup"><span data-stu-id="a90ee-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
- <span data-ttu-id="a90ee-123">Zadejte absolutní cestu pro umístění souboru protokolu, která by měla být mimo veřejný adresář WebHost vroot, aby se zabránilo jeho přístupu externí stranou pomocí webového prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="a90ee-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="a90ee-124">Ve výchozím nastavení nejsou klíče a osobní údaje (PII), jako je uživatelské jméno a heslo, zaznamenány v trasování a protokolovaných zprávách.</span><span class="sxs-lookup"><span data-stu-id="a90ee-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="a90ee-125">Správce počítače však může `enableLoggingKnownPII` atribut v `machineSettings` elementu souboru Machine.config použít k povolení aplikací spuštěných v počítači k protokolování známých osobně identifikovatelných informací (PII) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a90ee-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 <span data-ttu-id="a90ee-126">Nasazovač aplikací pak `logKnownPii` může použít atribut v souboru App.config nebo Web.config k povolení protokolování pii následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a90ee-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
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
  
 <span data-ttu-id="a90ee-127">Pouze v případě, že obě nastavení jsou `true` pii protokolování povoleno.</span><span class="sxs-lookup"><span data-stu-id="a90ee-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="a90ee-128">Kombinace dvou přepínačů umožňuje flexibilitu protokolovat známé pii pro každou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a90ee-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="a90ee-129">Měli byste si být vědomi toho, že pokud zadáte dva nebo více vlastních zdrojů v konfiguračním souboru, budou přečteny pouze atributy prvního zdroje.</span><span class="sxs-lookup"><span data-stu-id="a90ee-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="a90ee-130">Ostatní jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="a90ee-130">The others are ignored.</span></span> <span data-ttu-id="a90ee-131">To znamená, že pro následující soubor App.config, PII není zaznamenána pro oba zdroje, i když protokolování PII je explicitně povolena pro druhý zdroj.</span><span class="sxs-lookup"><span data-stu-id="a90ee-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
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
  
 <span data-ttu-id="a90ee-132">Pokud `<machineSettings enableLoggingKnownPii="Boolean"/>` prvek existuje mimo soubor Machine.config, systém <xref:System.Configuration.ConfigurationErrorsException>vyvolá .</span><span class="sxs-lookup"><span data-stu-id="a90ee-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="a90ee-133">Změny jsou účinné pouze při spuštění nebo restartování aplikace.</span><span class="sxs-lookup"><span data-stu-id="a90ee-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="a90ee-134">Událost je zaznamenána při spuštění, pokud `true`jsou oba atributy nastaveny na .</span><span class="sxs-lookup"><span data-stu-id="a90ee-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="a90ee-135">Událost je také zaznamenána, `logKnownPii` pokud je nastavena na, `true` ale `enableLoggingKnownPii` je `false`.</span><span class="sxs-lookup"><span data-stu-id="a90ee-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="a90ee-136">Další informace o protokolování pii naleznete v tématu [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span><span class="sxs-lookup"><span data-stu-id="a90ee-136">For more information on PII logging, see [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="a90ee-137">Správce počítače a nasazovač aplikací by měli být při použití těchto dvou přepínačů velmi opatrní.</span><span class="sxs-lookup"><span data-stu-id="a90ee-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="a90ee-138">Pokud je povoleno protokolování PII, jsou zaznamenány bezpečnostní klíče a pii.</span><span class="sxs-lookup"><span data-stu-id="a90ee-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="a90ee-139">Pokud je zakázána, citlivá data a data specifická pro aplikaci jsou stále protokolována v záhlavích a tělech zpráv.</span><span class="sxs-lookup"><span data-stu-id="a90ee-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="a90ee-140">Podrobnější diskusi o ochraně osobních údajů a ochraně osobních údajů před odhalením naleznete [v tématu Ochrana osobních údajů uživatelů](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="a90ee-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="a90ee-141">Kromě toho ip adresa odesílatele zprávy je zaznamenána jednou za připojení pro přenosy orientované na připojení a jednou za zprávu odeslanou jinak.</span><span class="sxs-lookup"><span data-stu-id="a90ee-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="a90ee-142">To se provádí bez souhlasu odesílatele.</span><span class="sxs-lookup"><span data-stu-id="a90ee-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="a90ee-143">K tomuto protokolování však dochází pouze na úrovních informace nebo podrobné trasování, které nejsou výchozí nebo doporučené úrovně trasování v produkčním prostředí, s výjimkou živéladění.</span><span class="sxs-lookup"><span data-stu-id="a90ee-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a90ee-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="a90ee-144">See also</span></span>

- [<span data-ttu-id="a90ee-145">Trasování</span><span class="sxs-lookup"><span data-stu-id="a90ee-145">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)

---
title: Otázky zabezpečení a užitečné tipy pro trasování
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
author: BrucePerlerMS
ms.openlocfilehash: 51db352913999d5527ead5273e6488cd09d88670
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207796"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="ea5f7-102">Otázky zabezpečení a užitečné tipy pro trasování</span><span class="sxs-lookup"><span data-stu-id="ea5f7-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="ea5f7-103">Toto téma popisuje, jak můžete chránit citlivé informace z vystaven i užitečné tipy při použití webového hostitele.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="ea5f7-104">Vlastní naslouchací pomocí webového hostitele</span><span class="sxs-lookup"><span data-stu-id="ea5f7-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="ea5f7-105">Pokud vytváříte vlastní naslouchací proces trasování, byste měli vědět o možnosti, že trasování může dojít ke ztrátě v případě hostované webové služby.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="ea5f7-106">Dojde k recyklování WebHost vypne živý proces při má duplicitní.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="ea5f7-107">Však dva procesy však musí mít přístup ke stejným prostředkům nechystáte nějakou dobu, což závisí na typu naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="ea5f7-108">V tomto případě, `XmlWriterTraceListener` vytvoří nový soubor trasování pro druhý proces; zatímco spravuje více procesů v rámci stejné relace trasování událostí pro Windows a poskytuje přístup ke stejnému souboru.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="ea5f7-109">Pokud vlastní naslouchací proces neposkytuje podobné funkce, když je soubor uzamčen dva procesy může dojít ke ztrátě trasování.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="ea5f7-110">Jste měli také něco vědět, že vlastní naslouchací můžete trasování a posílání zpráv na lince, například vzdálenou databázi.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="ea5f7-111">Jako modul pro nasazení aplikace měli byste nakonfigurovat vlastní naslouchací procesy s ovládacím prvkem odpovídající přístup.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="ea5f7-112">Také byste měli použít ovládací prvek zabezpečení v žádné osobní údaje, které mohou být zveřejněny ve vzdáleném umístění.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="ea5f7-113">Protokolování citlivých informací</span><span class="sxs-lookup"><span data-stu-id="ea5f7-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="ea5f7-114">Trasování neobsahovala záhlaví zpráv, když je zpráva v oboru.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="ea5f7-115">Když je povoleno trasování, osobní údaje v hlavičkách specifické pro aplikace, jako je řetězec dotazu; a základní informace, jako je číslo platební karty, může být viditelné v protokolech.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="ea5f7-116">Nástroje pro nasazení aplikace je zodpovědná za řízení přístupu na soubory konfigurace a sledování.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="ea5f7-117">Pokud nechcete, aby tento druh informací viditelný, měli zakázat trasování nebo odfiltrovat část dat, pokud chcete sdílet protokoly trasování.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="ea5f7-118">Následující tipy vám mohou pomoci při zabránit neúmyslnému zveřejnění obsahu souboru trasování:</span><span class="sxs-lookup"><span data-stu-id="ea5f7-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
-   <span data-ttu-id="ea5f7-119">Ujistěte se, že v protokolu, které soubory jsou chráněné pomocí řízení přístupu obsahuje seznam (ACL) ve webového hostitele i scénáře hostování na vlastním serveru.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
-   <span data-ttu-id="ea5f7-120">Zvolte příponu souboru, která nelze zpracovat v snadno pomocí nějaké webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="ea5f7-121">Například přípona souboru .xml není bezpečná volba.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="ea5f7-122">Příručka věnovaná IIS zobrazíte seznam přípon, které se dají obsluhovat můžete zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
-   <span data-ttu-id="ea5f7-123">Zadejte absolutní cestu k umístění souboru protokolu, který by měla být mimo virtuální kořenový adresář webového hostitele veřejného adresáře tak, aby přistupuje pomocí webového prohlížeče třetí strana.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="ea5f7-124">Ve výchozím nastavení klíče a identifikovatelné osobní údaje (PII) jako je například uživatelské jméno a heslo nejsou protokolovány v trasování a nezpůsobuje protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="ea5f7-125">Správce počítače, ale můžete použít `enableLoggingKnownPII` atribut `machineSettings` prvek souboru Machine.config tak, aby povolovala aplikace spuštěné na počítači pro přihlášení známého identifikovatelné osobní údaje (PII) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ea5f7-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>   
```  
  
 <span data-ttu-id="ea5f7-126">Pak můžete použít nástroje pro nasazení aplikace `logKnownPii` atributu v souboru App.config nebo Web.config povolení protokolování identifikovatelné osobní údaje následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ea5f7-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
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
  
 <span data-ttu-id="ea5f7-127">Pouze, pokud jsou obě nastavení `true` je povoleno protokolování identifikovatelné osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="ea5f7-128">Kombinací dvou přepínače umožňuje flexibilitu pro přihlášení známého PII pro každou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="ea5f7-129">Byste měli vědět, že pokud zadáte dvě nebo více vlastních zdrojů v konfiguračním souboru, se čtou jenom atributy první zdroj.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="ea5f7-130">Další se ignorují.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-130">The others are ignored.</span></span> <span data-ttu-id="ea5f7-131">To znamená, že pro následující App.config soubor, identifikovatelné osobní údaje se neprotokolují pro oba zdroje i v případě, že je explicitně povoleno protokolování identifikovatelné osobní údaje pro druhý zdroj.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
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
  
 <span data-ttu-id="ea5f7-132">Pokud `<machineSettings enableLoggingKnownPii="Boolean"/>` existuje element mimo souboru Machine.config, systém vyvolá <xref:System.Configuration.ConfigurationErrorsException>.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="ea5f7-133">Změny jsou platné pouze při spuštění nebo restartování aplikace.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="ea5f7-134">Událost se protokoluje při spuštění oba atributy jsou nastavena na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="ea5f7-135">Pokud je také zaznamenána událost `logKnownPii` je nastavena na `true` ale `enableLoggingKnownPii` je `false`.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="ea5f7-136">Další informace o protokolování identifikovatelné osobní údaje, najdete v části [bezpečnostní uzamčení PII](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-136">For more information on PII logging, see [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="ea5f7-137">Správce počítače a nástroje pro nasazení aplikace by měly využít extrémně opatrní při používání těchto dvou přepínače.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="ea5f7-138">Pokud je povoleno protokolování identifikovatelné osobní údaje, jsou protokolovány zabezpečení klíčů a identifikovatelné osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="ea5f7-139">Pokud je zakázaná, specifické pro aplikaci a citlivá data zaprotokolována v záhlaví zprávy a texty.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="ea5f7-140">Podrobnější informace o ochraně osobních údajů a ochranu identifikovatelné osobní údaje z vystaven, naleznete v tématu [ochrana osobních údajů uživatelů](https://go.microsoft.com/fwlink/?LinkID=94647).</span><span class="sxs-lookup"><span data-stu-id="ea5f7-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](https://go.microsoft.com/fwlink/?LinkID=94647).</span></span>  
  
 <span data-ttu-id="ea5f7-141">Navíc je IP adresa odesílatele zprávy zaprotokolována jednou za připojení pro přenosy tohoto připojení objektově orientovaného a jednou za jinak byla odeslána zpráva.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="ea5f7-142">To se provádí bez souhlasu odesílatele.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="ea5f7-143">Protokolování se však pouze dochází na úrovni informace nebo podrobné trasování, které nejsou výchozí nebo doporučená úrovní trasování v produkčním prostředí, s výjimkou živé ladění.</span><span class="sxs-lookup"><span data-stu-id="ea5f7-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea5f7-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea5f7-144">See Also</span></span>  
 [<span data-ttu-id="ea5f7-145">Trasování</span><span class="sxs-lookup"><span data-stu-id="ea5f7-145">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)

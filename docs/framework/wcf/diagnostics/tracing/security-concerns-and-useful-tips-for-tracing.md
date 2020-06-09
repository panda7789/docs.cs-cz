---
title: Otázky zabezpečení a užitečné tipy pro trasování
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 0a09e387a4f964441f11d07a84bd492345d5b691
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578874"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="6f3f0-102">Otázky zabezpečení a užitečné tipy pro trasování</span><span class="sxs-lookup"><span data-stu-id="6f3f0-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="6f3f0-103">V tomto tématu se dozvíte, jak můžete při použití webhosta chránit citlivé informace, které se zveřejňují, a užitečné tipy.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="6f3f0-104">Použití vlastního naslouchacího procesu trasování s webhostem</span><span class="sxs-lookup"><span data-stu-id="6f3f0-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="6f3f0-105">Při psaní vlastního naslouchacího procesu trasování byste si měli být vědomi možnosti, že trasování mohou být ztracena v případě služby hostované na webu.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="6f3f0-106">Když se webhost recykluje, vypne živý proces, zatímco dojde ke zdvojení.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="6f3f0-107">Nicméně dva procesy musí mít stále přístup ke stejnému prostředku, který je závislý na typu naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="6f3f0-108">V tomto případě `XmlWriterTraceListener` vytvoří nový trasovací soubor pro druhý proces; zatímco trasování událostí systému Windows spravuje více procesů v rámci stejné relace a poskytuje přístup ke stejnému souboru.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="6f3f0-109">Pokud váš vlastní naslouchací proces neposkytuje podobné funkce, trasování mohou být ztracena, pokud je soubor uzamčen dvěma procesy.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="6f3f0-110">Také byste si měli být vědomi, že vlastní naslouchací proces trasování může odesílat trasování a zprávy na lince, například do vzdálené databáze.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="6f3f0-111">Jako modul pro nasazení aplikace byste měli nakonfigurovat vlastní naslouchací procesy s odpovídajícím řízením přístupu.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="6f3f0-112">Měli byste také použít kontrolu zabezpečení na jakékoli osobní údaje, které mohou být zveřejněny ve vzdáleném umístění.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="6f3f0-113">Protokolování citlivých informací</span><span class="sxs-lookup"><span data-stu-id="6f3f0-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="6f3f0-114">Pokud je zpráva v oboru, trasování obsahují záhlaví zpráv.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="6f3f0-115">Pokud je povoleno trasování, osobní informace v hlavičkách specifických pro danou aplikaci, například řetězec dotazu; a informace o textu, jako je číslo platební karty, se můžou v protokolech zobrazit.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="6f3f0-116">Nástroj pro nasazení aplikace zodpovídá za vynucování řízení přístupu pro konfigurační a trasovací soubory.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="6f3f0-117">Pokud nechcete, aby se tyto informace zobrazovaly, měli byste zakázat trasování nebo odfiltrovat část dat, pokud chcete sdílet protokoly trasování.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="6f3f0-118">Následující tipy vám pomůžou zabránit neúmyslnému zpřístupnění obsahu trasovacího souboru:</span><span class="sxs-lookup"><span data-stu-id="6f3f0-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
- <span data-ttu-id="6f3f0-119">Zajistěte, aby byly soubory protokolu chráněny seznamem Access Control (seznam ACL) jak v hostování webhost, tak i v samostatných hostitelských scénářích.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
- <span data-ttu-id="6f3f0-120">Vyberte příponu souboru, kterou nelze snadno zpracovat pomocí webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="6f3f0-121">Například Přípona souboru. XML není bezpečná volba.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="6f3f0-122">Seznam rozšíření, která je možné zpracovat, najdete v příručce pro správu služby IIS.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
- <span data-ttu-id="6f3f0-123">Zadejte absolutní cestu pro umístění souboru protokolu, který by měl být mimo veřejný adresář website vroot, aby k němu externí strana nezískala přes webový prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="6f3f0-124">Ve výchozím nastavení klíče a identifikovatelné osobní údaje (PII), jako je uživatelské jméno a heslo, se v trasování a zprávách protokolu neprotokolují.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="6f3f0-125">Správce počítače však může použít `enableLoggingKnownPII` atribut v `machineSettings` prvku souboru Machine. config, aby umožňoval aplikacím běžícím na počítači protokolovat známé identifikovatelné osobní údaje (PII) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6f3f0-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 <span data-ttu-id="6f3f0-126">Nástroj pro nasazení aplikace může potom pomocí `logKnownPii` atributu v souboru App. config nebo Web. config povolit protokolování PII následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6f3f0-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
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
  
 <span data-ttu-id="6f3f0-127">Pouze v případě, že jsou obě nastavení `true` povolena protokolování PII.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="6f3f0-128">Kombinace dvou přepínačů umožňuje pružně protokolovat známé PII pro každou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="6f3f0-129">Měli byste si uvědomit, že pokud v konfiguračním souboru zadáte dva nebo více vlastních zdrojů, budou čteny pouze atributy prvního zdroje.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="6f3f0-130">Ostatní jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-130">The others are ignored.</span></span> <span data-ttu-id="6f3f0-131">To znamená, že pro následující soubor App. config není k dispozici protokol PII pro oba zdroje, i když je protokolování PII pro druhý zdroj explicitně povoleno.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
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
  
 <span data-ttu-id="6f3f0-132">Pokud `<machineSettings enableLoggingKnownPii="Boolean"/>` element existuje mimo soubor Machine. config, vyvolá systém <xref:System.Configuration.ConfigurationErrorsException> .</span><span class="sxs-lookup"><span data-stu-id="6f3f0-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="6f3f0-133">Změny jsou platné pouze v případě, že je aplikace spuštěna nebo restartována.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="6f3f0-134">Při spuštění se protokoluje událost, když jsou oba atributy nastavené na `true` .</span><span class="sxs-lookup"><span data-stu-id="6f3f0-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="6f3f0-135">Událost je také zaznamenána v případě `logKnownPii` , že je nastavena na, `true` ale `enableLoggingKnownPii` je `false` .</span><span class="sxs-lookup"><span data-stu-id="6f3f0-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="6f3f0-136">Další informace o přihlašování PII najdete v ukázce [zabezpečení PII](../../samples/pii-security-lockdown.md) – ukázka.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-136">For more information on PII logging, see [PII Security Lockdown](../../samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="6f3f0-137">Při použití těchto dvou přepínačů by měl správce počítače a nástroj pro nasazení aplikace velmi opatrní.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="6f3f0-138">Pokud je povolené protokolování PII, zaprotokolují se bezpečnostní klíče a PII.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="6f3f0-139">Pokud je zakázaná, citlivá a data specifická pro aplikaci se pořád přihlásí k hlavičkám a institucím zpráv.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="6f3f0-140">Podrobnější diskuzi o ochraně osobních údajů a ochraně PII, která se zveřejňují, najdete v tématu [Ochrana osobních údajů uživatele](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="6f3f0-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="6f3f0-141">Kromě toho se IP adresa odesílatele zprávy zaznamenává jednou za připojení pro přenosy orientované na připojení a jednou pro každou zprávu se poslalo jinak.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="6f3f0-142">To se provádí bez souhlasu odesílatele.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="6f3f0-143">Nicméně k tomuto protokolování dochází pouze na úrovních informace nebo podrobné trasování, které nejsou výchozí ani Doporučené úrovně trasování v produkčním prostředí, s výjimkou živého ladění.</span><span class="sxs-lookup"><span data-stu-id="6f3f0-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f3f0-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f3f0-144">See also</span></span>

- [<span data-ttu-id="6f3f0-145">Trasování</span><span class="sxs-lookup"><span data-stu-id="6f3f0-145">Tracing</span></span>](index.md)

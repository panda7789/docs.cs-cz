---
title: Zajištění zabezpečení pro protokolování zpráv
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: bb1a6ab84ceba27b398d397b4407a55aa02c4cae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185763"
---
# <a name="security-concerns-for-message-logging"></a>Zajištění zabezpečení pro protokolování zpráv
Toto téma popisuje, jak můžete chránit citlivá data před vystavením v protokolech zpráv, stejně jako události generované protokolováním zpráv.  
  
## <a name="security-concerns"></a>Obavy o bezpečnost  
  
### <a name="logging-sensitive-information"></a>Protokolování citlivých informací  
 Windows Communication Foundation (WCF) nemění žádná data v hlavičkách a tělespecifické pro aplikaci. WCF také nesleduje osobní údaje v hlavičkách specifických pro aplikaci nebo v tělových datech.  
  
 Pokud je povoleno protokolování zpráv, osobní informace v hlavičkách specifických pro aplikaci, jako je například řetězec dotazu; a informace o těle, jako je číslo kreditní karty, mohou být viditelné v protokolech. Nasazovač aplikací je zodpovědný za vynucení řízení přístupu v souborech konfigurace a protokolu. Pokud nechcete, aby byl tento druh informací viditelný, měli byste zakázat protokolování nebo odfiltrovat část dat, pokud chcete sdílet protokoly.  
  
 Následující tipy vám mohou pomoci zabránit neúmyslnému vystavení obsahu souboru protokolu:  
  
- Ujistěte se, že soubory protokolu jsou chráněny seznamy řízení přístupu (ACL) ve scénářích web-host i self-host.  
  
- Zvolte příponu souboru, kterou nelze snadno obsluhovat pomocí webového požadavku. Například přípona souboru XML není bezpečnou volbou. Seznam přípon, které se dají obsluhovat, najdete v příručce pro právu Internetové informační služby (IIS).  
  
- Zadejte absolutní cestu pro umístění souboru protokolu, která by měla být mimo veřejný adresář vroot webového hostitele, aby se zabránilo jeho přístupu externí stranou pomocí webového prohlížeče.  
  
 Ve výchozím nastavení nejsou klíče a osobní údaje (PII), jako je uživatelské jméno a heslo, zaznamenány v trasování a protokolovaných zprávách. Správce počítače však může `enableLoggingKnownPII` použít atribut `machineSettings` v elementu souboru Machine.config k povolení aplikací spuštěných v počítači k protokolování známých osobně identifikovatelných informací (PII). Následující konfigurace ukazuje, jak to provést:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>
```  
  
 Nasazovač aplikací pak `logKnownPii` může použít atribut v souboru App.config nebo Web.config k povolení protokolování pii následujícím způsobem:  
  
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
  
 Pouze v případě, že obě nastavení jsou `true` pii protokolování povoleno. Kombinace dvou přepínačů umožňuje flexibilitu protokolovat známé pii pro každou aplikaci.  
  
> [!IMPORTANT]
> V [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `logEntireMessage` a `logKnownPii` příznaky musí být `true` také nastavena na v souboru Web.config nebo App.config souboru povolit protokolování PII, jak je uvedeno v následujícím příkladu `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
 Měli byste si být vědomi toho, že pokud zadáte dva nebo více vlastních zdrojů v konfiguračním souboru, budou přečteny pouze atributy prvního zdroje. Ostatní jsou ignorovány. To znamená, že pro následující soubor App.config, PII není zaznamenána pro oba zdroje, i když protokolování PII je explicitně povolena pro druhý zdroj.  
  
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
                 <add name="traces"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\traces.svclog" />  
              </listeners>  
      </source>  
   </sources>  
</system.diagnostics>  
```  
  
 Pokud `<machineSettings enableLoggingKnownPii="Boolean"/>` prvek existuje mimo soubor Machine.config, systém <xref:System.Configuration.ConfigurationErrorsException>vyvolá .  
  
 Změny jsou účinné pouze při spuštění nebo restartování aplikace. Událost je zaznamenána při spuštění, pokud `true`jsou oba atributy nastaveny na . Událost je také zaznamenána, `logKnownPii` pokud je nastavena na, `true` ale `enableLoggingKnownPii` je `false`.  
  
 Správce počítače a nasazovač aplikací by měli být při použití těchto dvou přepínačů velmi opatrní. Pokud je povoleno protokolování PII, jsou zaznamenány bezpečnostní klíče a pii. Pokud je zakázána, citlivá data a data specifická pro aplikaci jsou stále protokolována v záhlavích a tělech zpráv. Podrobnější diskusi o ochraně osobních údajů a ochraně osobních údajů před odhalením naleznete [v tématu Ochrana osobních údajů uživatelů](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
> [!CAUTION]
> PiI není skryta v poškozených zpráv. Tyto messaged jsou zaznamenány jako-je bez jakýchkoliv úprav. Dříve uvedené atributy na to nemají žádný vliv.  
  
### <a name="custom-trace-listener"></a>Vlastní naslouchací proces trasování  
 Přidání vlastního naslouchacího procesu trasování ve zdroji trasování Protokolování zpráv je oprávnění, které by mělo být omezeno na správce. Důvodem je, že škodlivé vlastní naslouchací procesy lze nakonfigurovat tak, aby odesílat zprávy vzdáleně, což vede k zpřístupnění citlivých informací. Kromě toho pokud nakonfigurujete vlastní naslouchací proces pro odesílání zpráv na lince, například do vzdálené databáze, měli byste vynutit správné řízení přístupu v protokolech zpráv ve vzdáleném počítači.  
  
## <a name="events-triggered-by-message-logging"></a>Události aktivované protokolováním zpráv  
 V následujícím seznamu jsou uvedeny všechny události vyzařované protokolováním zpráv.  
  
- Přihlášení zpráv: Tato událost je vyzařována, když je protokolování zpráv povoleno v konfiguraci nebo prostřednictvím služby WMI. Obsah události je "Protokolování zpráv bylo zapnuto. Citlivé informace mohou být zaznamenány ve prostém textu, i když byly zašifrovány v drátě, například těla zpráv."  
  
- Odhlášení zpráv: Tato událost je vyzařována, když je protokolování zpráv zakázáno prostřednictvím služby WMI. Obsah události je "Protokolování zpráv bylo vypnuto."  
  
- Protokolovat známé osobní údaje zapnuto: Tato událost je vyzařována, když je povoleno protokolování známých pii. K tomu `enableLoggingKnownPii` dochází, `machineSettings` když je atribut v elementu `true`souboru `logKnownPii` Machine.config nastaven na hodnotu a atribut `source` prvku v `true`souboru App.config nebo Web.config je nastaven na hodnotu .  
  
- Protokolovat známé pii není povoleno: Tato událost je vyzařována při protokolování známých PII není povoleno. K tomu `logKnownPii` dochází, `source` když je atribut prvku v souboru App.config `true`nebo `enableLoggingKnownPii` Web.config nastaven na hodnotu , ale atribut v `machineSettings` elementu souboru Machine.config je nastaven na hodnotu `false`. Žádná výjimka se nevyvolá.  
  
 Tyto události lze zobrazit v nástroji Prohlížeč událostí, který je dodáván se systémem Windows. Další informace naleznete v tématu [Protokolování událostí](./event-logging/index.md).  
  
## <a name="see-also"></a>Viz také

- [Protokolování zpráv](message-logging.md)
- [Otázky zabezpečení a užitečné tipy pro trasování](./tracing/security-concerns-and-useful-tips-for-tracing.md)
